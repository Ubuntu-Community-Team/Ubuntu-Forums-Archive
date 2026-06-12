---
title: "A few simple shell scripting questions about variables, ftp etc."
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Bluecircle on 2007-06-22
Hello, I'm trying to make a stats page that uploads to a website, here is the script that creates the page so far:

make_file
```

#!/bin/bash

# make_page - A script to produce an HTML file

title="Current stats"

uptime=$(uptime)

disk=$(sudo fdisk -l)

cat <<- _EOF_
    <HTML>
    <HEAD>
        <TITLE>
        $title
        </TITLE>
    </HEAD>

    <BODY>
    <H1>$title for $HOSTNAME</H1>
<br>
<br>
	$uptime
<br>
<br>
	$disk
<br>
    </BODY>
    </HTML>
_EOF_
       

```

stats
```

#!/bin/bash

# stats - runs make_file and then ftp_upload

sudo su

cd bin/

./make_file > index.html

./ftp_upload

exit 0

```

ftp_upload
```

#!/bin/bash

# ftp_upload - uploads index.html to my website

ftp
open x.x.com
user x pass
cd /webdir/
put /home/brian/bin/index.html index.html
disconnect
exit 0

```

Also, when writing a shell script using ftp, how do I issue commands to ftp? Once ftp is issued, I get:
>

i can manually type the commands, but I haven't figured out how to do it from a script.



I would like to have it set up like this:

stats - runs make_file every x minutes
make_file - creates index.php with updated stats information (needs root privileges to do some commands)
ftp_upload - opens an ftp and uploads index.php, then exits

I guess running stats as root would lets make_file have the needed privileges to run root commands.

Edit: I assume I need to make a loop to make stats run every x minutes. How can I do this?

Thanks for helping, I'm obviously new at this ;)

---

### Post by Bachstelze on 2007-06-22
1. To pass the output of a comand, you use parenthese, like this : $(uptime), $(sudo fdisk -l).

2. Does your distant machine run a SSH server ? If you, you can use scp to copy it with out any input.

---

### Post by Bluecircle on 2007-06-22
> **HymnToLife said:**
> 1. To pass the output of a comand, you use parenthese, like this : $(uptime), $(sudo fdisk -l).

2. Does your distant machine run a SSH server ? If you, you can use scp to copy it with out any input.

Thanks, I just figured tht out. (script updated).

Yes, i does run ssh, how would I do that?

---

### Post by Bluecircle on 2007-06-22
edit: post removed, problem fixed.

---

### Post by Bluecircle on 2007-06-23
Ok heres the update:

stats:
```

#!/bin/bash

# stats - A script to produce a HTML file and upload it to a remote server

cd /home/brian/bin/stats/

./make_page > index.html

scp $HOME/bin/stats/index.html nointernet@rossmore.dreamhost.com:nointer.net/index.html

exit 0

```


make_page
```

#!/bin/bash

# make_page - A script tomake index.html


title="Current stats"

RIGHT_NOW=$(date +"%x %r %Z")

uptime=$(uptime)

uname=$(uname -a)

disk=$(sudo fdisk -l)

mem=$(cat /proc/meminfo)

cpu=$(cat /proc/cpuinfo)

ps=$(pstree)

cat <<- _EOF_

    <HTML>
    <HEAD>
        <TITLE>
        $title
        </TITLE>
    </HEAD>

    <BODY>
    <H2>$title for $HOSTNAME updated on $RIGHT_NOW</H2>
<br>
<br>
	<b>Uptime</b>
<br><br>
	<pre>$uptime</pre>
<br>
<br>
	<b>System Information</b>
<br><br>
	<pre>$uname</pre>
<br>
<br>
<br>
	<b>Disk Info</b>
<br><br>
	<pre>$disk</pre>
<br>
<br>
<br>
	<b>Tree of Running Processes</b>
<br><br>
	<pre>$ps</pre>
<br>
<br>
<br>
	<b>CPU Info</b>
<br><br>
	<pre>$cpu</pre>
<br>
<br>
<br>
	<b>Memory Info</b>
<br><br>
	<pre>$mem</pre>
<br>
<br>
<br>
    </BODY>
    </HTML>
_EOF_

exit 0

```

I have scp working with a public key and everything. The only thing I need to know is:

How can I make this automatically run every 15 minutes, and keep sudo permissions?

---

### Post by kevdog on 2007-06-23
Set up a cron job that runs the script every 15 minutes -- this is the easiest way!  You will need the cron daemon installed and then you will need to make and edit your crontab file.

---

### Post by Bluecircle on 2007-06-23
> **kevdog said:**
> Set up a cron job that runs the script every 15 minutes -- this is the easiest way!  You will need the cron daemon installed and then you will need to make and edit your crontab file.

Ok, got crontab working. Now finally, what should I do about it prompting me for the sudo password? How can I give it permissions once and then not have it do that again.

---

