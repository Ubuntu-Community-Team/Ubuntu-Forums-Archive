---
title: "FTP programs freeze at &quot;Accepted data connection&quot;"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by sphism on 2007-09-24
Hello,

I'm going nuts. :(

I switched to ubuntu a few months back, i love it.

I've been using the nautilus ftp features (places>connect to server and all that stuff)

Also love that I can SSH by the same method

everything was working great.

PROBLEM:

In nautilus : Sometimes when I copy a file it deletes the server file but never completes the upload

so i tried gftp : Same thing, never completes

so i try fireFTP : it just gets as far as 'Accepted data connection'

NOTE: i can see the files on the server, i can even download them.

The wierdest thing is it seems totally random. It started just doing it occasionally, but now there's certain files i just cannot upload.

I managed to upload a file a few times, then replaced the text in the file and it doesn't work.

I've searched the forums, tried lots of things but i'm totlaly stuck, i've got a stack of web work to do and this is a real pain.

I wondered if it might be a firewall issue?

Or i have recently installed LAMP on my laptop?

I run 64bit ubuntu and have firefox and swiftfox32 running, there seems to be some strangeness going on between the 2, could that be a problem?

File permissions on the local folder?

erm???

Big thanks to anyone who can help.

matt

---

### Post by Pumalite on 2007-09-24
See if you can find anything useful here:

[http://www.smartftp.com/forums/lofiversion/index.php?f14-1950.html](http://www.smartftp.com/forums/lofiversion/index.php?f14-1950.html)

---

### Post by the.phantom on 2007-09-24
i've had troubles every once in a while with fireftp
and found it was the permission of the file

i keep my upload/download files in the home folder
and they are showing rw-r-r in fireftp

---

### Post by sphism on 2007-09-24
Thanks for the help,

that smartftp site looks good i'll have a good look thru there later.

I don't think it's fireFTP that's the problem since all ftp software seems to be the same.

I just moved the folder into my home folder (i had moved everything into /var/www/ so that apache could show them to me)

I set permissions so i had access to everything. Uploaded a file twice. Then i edited it with gedit. Uploaded again in nautilus and nothing, just get

Copying file : 1 of 1 (0:00 Remaining)
 eventually it returns an error

with gFTP i get no upload either

It's weird that both seem to get the file uploaded then fail just before resolving it all on the server,

any other ideas?

here's the log from gftp:

the progress output says: Sent 5,383 of 5,383, transfer stalled, unknown time remaining

(sometimes is does this and then completes)

LOG:

220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 104 of 800 allowed.
220-Local time is now 20:32. Server port: 21.
220-This is a private system - No anonymous login
220 You will be disconnected after 15 minutes of inactivity.
USER XXXX

331 User XXXX OK. Password required
PASS xxxx
230-User XXXX has group access to:  8761    
230 OK. Current directory is /
SYST

215 UNIX Type: L8
TYPE I

200 TYPE is now 8-bit binary
PWD

257 "/" is your current location
Loading directory listing / from server (LC_TIME=en_NZ.UTF-8)
PASV

227 Entering Passive Mode (64,13,192,188,228,18)
LIST -aL

150 Accepted data connection
226-ASCII
226-Options: -a -l 
226 9 matches total
Successfully changed local directory to /home/matt/work
Successfully changed local directory to /home/matt/work/pyroptix
CWD /html

250 OK. Current directory is /html
PWD

257 "/html" is your current location
Loading directory listing /html from server (LC_TIME=en_NZ.UTF-8)
PASV

227 Entering Passive Mode (64,13,192,188,231,211)
LIST -aL

150 Accepted data connection
226-ASCII
226-Options: -a -l 
226 88 matches total
DELE /html/noflashnew.php

250 Deleted /html/noflashnew.php
DELE /html/noflashnew2.php

250 Deleted /html/noflashnew2.php
Loading directory listing /html from server (LC_TIME=en_NZ.UTF-8)
PASV

227 Entering Passive Mode (64,13,192,188,219,80)
LIST -aL

150 Accepted data connection
226-ASCII
226-Options: -a -l 
226 86 matches total
Loading directory listing /html from cache (LC_TIME=en_NZ.UTF-8)
PASV

227 Entering Passive Mode (64,13,192,188,196,122)
STOR /html/noflashnew2.php

150 Accepted data connection
Connection to ftp.pyroptix.com timed out
Disconnecting from site ftp.pyroptix.com
There was an error transfering the file /home/matt/work/pyroptix/noflashnew2.php

---

### Post by the.phantom on 2007-09-25
just a hunch as i am no way a ftp expert !
but you show this

226-ASCII

a easy thing to try would change it 
in fireftp and usually the others you can select "auto" or binary

i'm not on my other systems but think all are set to auto? not sure 
and would not take much to try

---

