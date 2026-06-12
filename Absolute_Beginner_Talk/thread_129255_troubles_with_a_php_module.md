---
title: "troubles with a php module"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2006-02-13
Ok.. maybe this should go under "server talk" bu i think this is a very basic question so...

php4-imap its installed and updated but its not working 

[PHP]Warning: imap_open(): Couldn't open stream ****** in /var/www/2006.02.13/login.php on line 11[/PHP]

should i edit any conf file to tell apache or php that php4-imap exists?

how to instal php4-imap porperly?

i read the wiki and the thread pointed there bu the problem is diferent. I have php4-imap already installed but not working.

i installed the module using apt-get

```
sudo apt-get install php4-imap
```

but i think it takes more than this to have it working.

help! thx in advance

---

### Post by nihilocrat on 2006-02-13
Hmm... it looks like the module is probably installed correctly since the error message is complaining about the input, rather than the nonexistence of the function. Make sure it's installed or not by making a script real quick which only has the line 'phpinfo();' in it and looking at it in a web browser. Search the file for 'imap' and if it brings you to a bunch of configuration info, it's installed.

Otherwise, I guess you would need to double-check your php.ini file to see if it's enabling the module. There should be a line somewhere in there like 'extension=imap.so'.

---

### Post by pedrotuga on 2006-02-13
phpinfo outpusts this

```
imap
IMAP c-Client Version 	2001
SSL Support 	enabled
Kerberos Support 	enabled

```

and that line its the last line of php.ini so it should be everything ok.
But no way the script input of imap_open() is wrong... the script works in my local computer :( not on my server...

---

