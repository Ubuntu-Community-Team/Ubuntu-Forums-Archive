---
title: "Users administering their own email addresses"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Roo on 2007-11-21
What I want to do:

Run an Ubuntu (Dapper) email server - using Postfix.  This is my home email server - so low number of users.  However, as a spam protection method, I want to make it trivial for users of this system (my wife) to manager email aliases.

_What I've found so far:_
1) MailMan apparently can be setup do something like this.  From what I've seen, it would be massive overkill.  
2) Root access required - add new alias to /etc/aliases and run newaliases.

I'm tempted to cook up some PHP or similar to drive a solution based on (2).  I'd probably cook up a setuid program/script to add an alias.  Then do some PHP magic or something.

_The ideal solution:_
  Web UI
  Some sort of authentication (could be apache based)
  Cookie based for user information / access (optional)
  Users would need to query existing aliases against their email address.
  Users can add new alias. (optional - allow comments to be associated with alias)
  Users can delete an alias.

I'm posting here because I want to avoid re-inventing the wheel.  I'm sure that WebMin can do this for me as well - but what I'm really looking for is something very simple (and foolproof).

Thanks - Roo

---

### Post by Roo on 2007-12-17
I ended up rolling a DIY solution.  I figure I'd document in case anyone stumbled across this posting with the same problem.

There are 2 parts to my solution.  A small C program that is setuid (via chmod +s) and a PHP/HTML script.

For security - I use apache to control access.

First the C program installed in /usr/local/bin/addalias 
```

/*
 * setuid scripts have serious security issues, so this
 * is a very trivial C program to append 2 lines to /etc/aliases
 * based on data passed on the command line.  It then exec's
 * postalias to update the email aliases.
 */

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>

#define ETC_ALIASES "/etc/aliases"

int main( int argc, char **argv ) {
        FILE *aliases;

        if( argc != 4 ) {
                fprintf( stderr, "Usage: %s <user> <alias> <comment>\n", argv[0] );
                exit( -1 );
        }

        aliases = fopen( ETC_ALIASES, "a" );
        if( NULL == aliases ) {
                fprintf( stderr, "fopen() failed: %s\n", strerror(errno));
                exit( -2 );
        }
        fprintf( aliases, "# %s\n", argv[3] );
        fprintf( aliases, "%s:\t%s\n", argv[2], argv[1] );
        fclose( aliases );

        /* exec() postalias  - this will not return on success */
        execl( "/usr/sbin/postalias", "/usr/sbin/postalais", ETC_ALIASES, NULL );

        fprintf( stderr, "execl() failed: %s\n", strerror(errno) );
}

```

And now the PHP/HTML script
```

<?php
$user = $_POST['user'];
$alias = $_POST['alias'];
$comment = $_POST['comment'];
if (!isset($_POST['submit'])) { 
/* 
 * If page is not submitted to itself echo the form
 */
?>
<html>
<head>
<title>New Email Alias</title>
</head>
<body>
<form method="post" action="<?php echo $PHP_SELF;?>">
Email Address: 
<select name="user" size="1">
<option value="frank">frank
<option value="bob">bob
</select>
New Alias: <input type="text" size="12" maxlength="36" name="alias"><br />
Comment: <input type="text" size="80" maxlength="80" name="comment"><br />
<input type="submit" value="Create New Alias" name="submit">
</form>
<br/>
Contents of existing alias file are below the line. 
<hr>
<?
/* Now here we want to dump known /etc/aliases data */
$lines= file('/etc/aliases');
foreach ($lines as $line_num => $line) {
    echo $line . "<br />";
}

} else {
/*
 *      Start of the submit portion 
 */
unset($_POST['submit']);

if (($alias != "" ) && ($comment != ""))  {

echo "User: " . $user . "@mydomain.com<br />";
echo "Alias: " . $alias. "@mydomain.com<br />";
echo "Comment: " . $comment. "<br />";
/* Use system as postalias will warn us when there is a problem */
system( "/usr/local/bin/addalias " . $user . " " . $alias . " \"" . stripslashes($comment) . "\"" );
} else {
echo "Error: You must supply a value for both alias and comment.";
} 
?>
<form>
<input type="button" value="Done" onclick="window.location.href='<? echo "https://www.mydomain.com" . $_SERVER['REQUEST_URI'] . "'"?>">
</form>
<?
} /* end of submit portion */
?>


```

---

