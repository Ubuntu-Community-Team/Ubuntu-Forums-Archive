---
title: "Login name redirects?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by windle on 2008-02-06
hi is it possible for .htaccess to recognise someones sucessfull login and redirect them to their own personal folder?

I.E 

user comes to a .htaccess normal login page [www.mydomain.com/login](www.mydomain.com/login)

they type in their name fred and their password, if its sucessfull it redirects fred to [www.mydomain.com/login/fred](www.mydomain.com/login/fred) and only fred has access due to another .htaccess file in there. 

can .htaccess handle that or do i need something else like php to handle that for me?

Thanks

---

### Post by marufaberlin on 2008-02-06
You can program that with php. What exatly do you want to do?

---

### Post by marufaberlin on 2008-02-06
Maybe you should have a look at some content management systems, like drupal, joomla or typo3. They can do the user management for you. For Drupal, you could easily write a PHP script that redirects to the folder.

---

### Post by windle on 2008-02-06
if possible i would sooner not use php but i can and have used it in the past. 

basically as below a website with say 500 users i dont want to have a list where people come along and simply click their name and then login. I want them all to see 1 login box and depends who logs in, goes to the right directory

fred see's [www.mydomain.com/login](www.mydomain.com/login) then he is redirected to [www.mydomain.com/fred](www.mydomain.com/fred)

paul see's [www.mydomain.com/login](www.mydomain.com/login) then he is redirected to [www.mydoamin.com/paul](www.mydoamin.com/paul) 

if that makes sence? 

Thanks:)

---

### Post by windle on 2008-02-06
can i add some php scripting into the .htaccess documents? i dont want to have 2 sets of passwords floating about really. 

[www.mydomain.com/login](www.mydomain.com/login) is protected with .htaccess and so is [www.mydomain.com/login/test](www.mydomain.com/login/test)

the next step is to give certain people access just to their own folders without having to list 500 people. fred sucess full login gives him access to his area only :)

---

### Post by marufaberlin on 2008-02-06
All you need is the login script to redirect the user? Nothing else? Then either you use the PHP-inbuilt session management or write your own. If you don't need SSL secure connections, I won't use .htacces.

---

### Post by marufaberlin on 2008-02-06
Have a look at drupal.org for something like that. Makes things incredibly easier.

---

### Post by windle on 2008-02-06
so bin .htaccess completely and use justs a php login system would be better? with mysql access? 

any samples i can try ? 

Thanks

---

### Post by marufaberlin on 2008-02-06
Hang on - what server do you use? Is PHP safe mode on?

---

### Post by windle on 2008-02-06
1 have kind of 3 areas to look at 

1. is an area where certain groups have access to see things
2. a user area where only that user has access too
3. at a later date i would like to make 1 user access their files stored on a totally different computer. More of an link back to their files on a LAN not the web server?

do it all with the web management software ?

---

### Post by windle on 2008-02-06
i have my own windows 2003 server located in a data center it runs iis and apache but the later is only so i can use .htaccess if i was to use the web management i suppose i can bin the apache off?

---

### Post by marufaberlin on 2008-02-06
drupal does all of it. You might have to install some modules to do 3) but the user and group access management is already built in.

---

### Post by windle on 2008-02-06
i will certainly give it a look now :) thanks

---

### Post by marufaberlin on 2008-02-06
I wouldn't use IIS, its exploited in less than 2 minutes. Apache is fine. 

PS.: why do you post in an ubuntu forum if you use WinDoze???:confused:

---

### Post by windle on 2008-02-06
iis is only using the public side of things. I then use apache for any logging in stuff. 

good question he he i searched and found here i know its not windows but you seam to be a busy forum so thought i would give it a shot :)

tried drupal didn;t do exactly what i wanted so dont think thats the right thing for me. Will try the other 2 mentioned see if its any better.

i think my .htaccess is best least i can keep the theme of my website easy enough that way. Just need a php script to redirect i think ?

---

### Post by marufaberlin on 2008-02-07
Well... how do you do your login stuff?

That's how I would do it:
Write a PHP script that does login, checks password and username in a MySQL or PostgreSQL Database, and then sends a referrer tag to the browser, depending on the data in one column in the Table.

For Example, if you have a table like this:

```

+-----------+----------+-----------------+
| Username  | Password | Referrer        |
+-----------+----------+-----------------+
| fred      | Pass     | /fred/index.php |
+-----------+----------+-----------------+

```

Then if user "Fred" logs in with password "Pass" (be sure to use md5 sums or some other secure technique) then he should be redirected to /fred/index.php.
That would be my approach, but you can do it differently, of course.

---

### Post by whazooo on 2008-02-07
The problem your going to run into using .htaccess is, the people will be able to
get into any of the other peoples folder after they have authenticated.
Example:
If joe blow authenticates and is redirected to his folder.
say 
[http://www.whatever.com/members/joe](http://www.whatever.com/members/joe)

Then without each folder having a separate .htaccess file, joe could then just add
mary to the end of the url in his browser to get into marys folder
[http://whatever.com/members/mary](http://whatever.com/members/mary)

If you dont care about that you could use apache rewrite to get it done like this:
```

AuthUserFile /path/to/.htpasswd
AuthName "Members Area"
AuthType Basic
Require valid-user

RewriteEngine on
RewriteCond %{REQUEST_URI} ^/members/?$
RewriteRule ^.*$ /members/%{REMOTE_USER}/ [L,R]

```

where joes folder would be located on your server here
[http://www.whatever.com/members/joe](http://www.whatever.com/members/joe)

This is an age old problem for webmasters which has been solved with the use of a php/perl/ladpp/mysql combination.

If you dont mind putting a .htaccess file in each folder, you can use a simple variable redirect in your html main page.

if you want a simple way to redirect via authenticated php,  you could do something like this:
```

<?php

$auth = false; // Assume user is not authenticated
$server = "www.whatever.com/members/"; // address to goto

if (isset( $PHP_AUTH_USER ) && isset($PHP_AUTH_PW)) {

    // Read the entire file into the variable $file_contents

    $filename = '/path/to/.htpasswd';
    $fp = fopen( $filename, 'r' );
    $file_contents = fread( $fp, filesize( $filename ) );
    fclose( $fp );

    // Place the individual lines from the file contents into an array.

    $lines = explode ( "\n", $file_contents );

    // Split each of the lines into a username and a password pair
    // and attempt to match them to $PHP_AUTH_USER and $PHP_AUTH_PW.

    foreach ( $lines as $line ) {

        list( $username, $password ) = explode( ':', $line );

        if ( $username == "$PHP_AUTH_USER" ) {

            // Get the salt from $password.
            //  first two characters of DES-encrypted string.

            $salt = substr( $password , 0 , 2 );

            // Encrypt $PHP_AUTH_PW based on $salt

            $enc_pw = crypt( $PHP_AUTH_PW, $salt );

            if ( $password == "$enc_pw" ) {

                // A match is found, meaning the user is authenticated.
                // Stop the search.

                $auth = true;
                break;

            }

        }
    }

}

if ( ! $auth ) {

    header( 'WWW-Authenticate: Basic realm="Private"' );
    header( 'HTTP/1.0 401 Unauthorized' );
    echo 'Authorization Required.';
    exit;

} else {

   header("Location: http://" . $server . $username); 
}

?>

```

---

### Post by windle on 2008-02-07
that looks exactley what i am after doing! can you point me in the right direction :)

i have used both php and mysql but i dont know how to call databases and passwords etc i have come accross this which looks like it does a good job?

[http://evolt.org/node/60384](http://evolt.org/node/60384)

---

### Post by windle on 2008-02-07
whazoo thats exactley what i wanted to know if it works ;)

i dont mind writting the .htaccess for each person so long as its only once he he. It makes my life in the future much easier :)

i will give it a shot later today and let you know. Thanks for what looks like is my answer :)

---

### Post by whazooo on 2008-02-07
> **windle said:**
> whazoo thats exactley what i wanted to know if it works ;)

i dont mind writting the .htaccess for each person so long as its only once he he. It makes my life in the future much easier :)

i will give it a shot later today and let you know. Thanks for what looks like is my answer :)

Windle;
Just remember, If you do it with apache redirect like above AND have an .htaccess file in each folder your people will have to authenticate twice.

---

### Post by windle on 2008-02-07
ah yes good thinking lol

i think the PHP below is probably the correct way of doing things then eh! 

Thanks will have a bash when i get some time today at it :)

---

### Post by whazooo on 2008-02-07
If you find that none of the posts here gets you to where you want to be, You might start a thread over at the programing talk forum
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by windle on 2008-02-07
cheers for you help. just had a thought. 

What if i were to use your .htaccess script as first point of call. and then from within each persons directory i could have the same page saying link to group 1 group 2 area. That way their authentication shouldnt ask again unless they are not aloud access of course ?

---

### Post by whazooo on 2008-02-07
I'm not sure what you mean here exactly.
And I dont know how you have these directories set up on your server.
but lets say you have it set up like this:


yourserver.com/members

/members/joe
/members/mary
where /members 
is protected. with an .htaccess file placed here:
yourserver.com/members/.htaccess

you will have a problem with joe being able to get to marys directory with out an .htaccess file in each of their directory's. If you put an .htaccess file in each of their directory's like so:
yourserver.com/members/joe/.htaccess the user will have to authenticate twice.

If however you have it set up like:
joe.yourserver.com/
mary.yourserver.com/

or

yourserver.com/j/joe
yourserver.com/m/mary

the apache  rewrite in the .htaccess "should" work without any further .htaccess files.

---

### Post by whazooo on 2008-02-07
Windle;
After rereading the entire post.
I think youi will be able to use the apache rewrite in the .htaccess file 
just as you have it now with no other stuff to do.

This is of course based on you having the rewrite module in apache compiled in.

---

### Post by windle on 2008-02-07
i get ya mate. i will certainly give it a shot tomrow. I can make the directory structure what ever i want so that should be fine:)

---

### Post by windle on 2008-02-11
hi i have just started to test the script from the last page

AuthUserFile /path/to/.htpasswd
AuthName "Members Area"
AuthType Basic
Require valid-user

RewriteEngine on
RewriteCond %{REQUEST_URI} ^/members/?$
RewriteRule ^.*$ /members/%{REMOTE_USER}/ [L,R]

however i get "Internal Server Error"

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, [email]admin@REMEXT.loca[/email]l and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.

I have changed the auth user path to what was there with my old .ht file at it works again. Something it doesnt like in that code?

---

### Post by windle on 2008-02-11
oops ignore that i had to enable rewrite in the apache doc. Its asking me for a password now which seams to be write. If i get it wrong asks me again. Howvwer with the correct passwords login i just get page cannot be displayed. it doesnt seam to be redirecting anywhere?

---

### Post by windle on 2008-02-11
hi i have also tried the php script below the .htaccess one. 

i can get it to ask for a password but it never authenticates. no matter what :(

can i build this into mysql instead of a .htaccess folder.

getting no where here :(

---

### Post by whazooo on 2008-02-11
Hi Windle,
The .htaccess should work as we talked about,
I tested it on my box before I replied.

Where is the location of .htaccess?
to do what we talked about, It needs to be in:
yourserver/members/
If you have it in:
yourserver/.htaaccess
or yourserver/someotherdirectory-exceptmembers/

it will not work.

---

### Post by whazooo on 2008-02-11
windle,
Try this php script, It should work better for you:
```

<?php 
    /**
     * Authenticate a user against a password file generated by Apache's httpasswd
     * using PHP rather than Apache itself.
     *
     * @param string $user The submitted user name - Nothing to do here
     * @param string $pass The submitted password - nothing to do here
     * @param string $pass_file='.htpasswd' - The system path to the htpasswd file
     * @param string $crypt_type='DES' The crypt type used to create the htpasswd file
     * @return bool
     * @$server Set this to where your members will go After Auth example: /var/www/members/
     */
     $server = "yourserver/members/";
    function http_authenticate($user,$pass,$pass_file='/var/www/.htpasswd',$crypt_type='DES'){
        // the stuff below is just an example useage that restricts
        // user names and passwords to only alpha-numeric characters.
        if(!ctype_alnum($user)){
            // invalid user name
            return FALSE;
        }
        
        if(!ctype_alnum($pass)){
            // invalid password
            return FALSE;
        }
        
        // get the information from the htpasswd file
        if(file_exists($pass_file) && is_readable($pass_file)){
            // the password file exists, open it
            if($fp=fopen($pass_file,'r')){
                while($line=fgets($fp)){
                    // for each line in the file remove line endings
                    $line=preg_replace('`[\r\n]$`','',$line);
                    list($fuser,$fpass)=explode(':',$line);
                    if($fuser==$user){
                        // the submitted user name matches this line
                        // in the file
                        switch($crypt_type){
                            case 'DES':
                                // the salt is the first 2
                                // characters for DES encryption
                                $salt=substr($fpass,0,2);
                                
                                // use the salt to encode the
                                // submitted password
                                $test_pw=crypt($pass,$salt);
                                break;
                            case 'PLAIN':
                                $test_pw=$pass;
                                break;
                            case 'SHA':
                            case 'MD5':
                            default:
                                // unsupported crypt type
                                fclose($fp);
                                return FALSE;
                        }
                        if($test_pw == $fpass){
                            // authentication success.
                            fclose($fp);
                            return TRUE;
                        }else{
                            return FALSE;
                        }
                    }
                }
                fclose($fp);
            }else{
                // could not open the password file
                return FALSE;
            }
        }else{
            return FALSE;
        }
    }
    header("Location: http://" . $server . $user);
?>

```

---

### Post by windle on 2008-02-12
hi wazoo i rebuild apache yesterday and then made the directories like you said with members and the .htaccess worked then:lolflag:

i am going to make a few new users and check to see permissions etc. 

i presume this is where the .htaccess in each folder comes in or the funny /j/joe extensions work ?

will have a mess about now.

Thanks you so much whazoo for your help and others:guitar:

---

### Post by windle on 2008-02-12
i have just tried the new php script whazoo, the page cannot be displayed is all i get from it?

---

### Post by marufaberlin on 2008-02-14
> ```

                            case 'SHA':
                            case 'MD5':
                            default:
                                // unsupported crypt type
                                fclose($fp);
                                return FALSE;

```

You may have noticed that there is no code for handling SHA or MD5 encryption.

Also, this script is designed for linux apache installations and uses folders that do not exist in WinDoze, like /var/www/. :-)

Maybe you forgot to change the > 
```
$server = "yourserver/members/"
```
line::-?

---

### Post by whazooo on 2008-02-14
I was under the assumption that he was using a xamp type setup which does provide a 
/var/www
for the root directory :-)

and was using something like;
[http://www.kxs.net/support/htaccess_pw.html](http://www.kxs.net/support/htaccess_pw.html)
for the username/password combo in the htpasswd file.

Of course all this is just for testing and not for production. 

Windle,
If your planing on using this set up for a production server, As I stated before,
You should ask over in the programing forum and let those more knowledgeable folks help ya out.

---

