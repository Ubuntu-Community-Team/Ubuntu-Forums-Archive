---
title: "permissions/ comple a tar file"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-07
first question

how to set permisions on the command line.

is it chmod -R

second question

also for moving tar files balls from desktop to home or etc directory
where should I complie make and install a tar file from should I be in the
home or etc directory.

thanks

lex1:???:

---

### Post by colo on 2006-03-07
Yes, you do set permission using "chmod" - it's a mnemonic short for "CHange MODe". You should know about the owner-group-others-scheme, or octal notation of UNIX permissions to operate it safely and successfully.
-> [http://www.perlfect.com/articles/chmod.shtml](http://www.perlfect.com/articles/chmod.shtml)


If you plan to actually INSTALL the compiled contents of a source-tarball, it's not important where to leave the extracted tarball at all. However, to keep track of what you've got on your machine, I suggest a hidden directory in your home-directory, possibly ~/.tarballs or so, to have your stuff compile there. It's also recommended to compile source as user, check the "install"-directive of the Makefile (if you know how to interprete it, at least :)), and THEN install the application as root.

Hope I covered what you were asking for :)

---

### Post by Sutekh on 2006-03-07
[QUOTE=lex1]first question

how to set permisions on the command line.

is it chmod -R
[/QUOTE]
What permissions do you wish to set?  You can do it several ways.

You can add permissions like
```
chmod +x
```
This adds executable permissions, or you could
```
chmod 750
```
This has full permissions for the file owner, read/execute permissions for the group owner and no permissions for everyone else

Have a look here for a permissions 'calculator'

[Unix chmod Permissions Calculator]("http://www.robolink.com/calculators10.htm")

[QUOTE=lex1]
second question

also for moving tar files balls from desktop to home or etc directory
where should I complie make and install a tar file from should I be in the
home or etc directory.

thanks

lex1:???:[/QUOTE]
Doesn't matter, when you *make* the program it should copy the compiled binary into /usr/bin or similar.  Compile it from your home for keeping track of everything you install

---

