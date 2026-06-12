---
title: "installing rpm,bin,bz2 etc files"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-05-31
how to install the following files

1-j2sdk-1.5-linux-rpm.bin
2-j2sdk-1.5-linux.bin

plz mention the commands for above two files so that the path of above should be same as files installed by apt-get.

what is the difference between file 1 and file 2.i can't understand.i think both are of same .bin type.

3-file.bz2
4-file.sh
5-file.jar

so far i have encountered these files.if there are someother types of files plz mention them .also tell me where does apt-get stores .deb filse when we download by apt-get and where does it installs them.are the files downloaded and installed by apt-get uptodate (newest versions).for example my wine says that it is six month old.unfortunately my proxy server is not allowing me to install winehq from their site.so i downloaded winehq old version and i think this old wouldn't be as six month.can i update my six month old wine without using winhq.com repository?

---

### Post by Jagot on 2006-05-31
This will help with installing:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by PriceChild on 2006-05-31
Not that you shouldn't be finding out about all those, but what's wrong with just sticking with .deb as much as possible and using simply "dpkg -i >>name>>.deb" when you need to install them... If they're not already in the repos?

I haven't needed to digress :S Those files are java aren't they? that's all in the repos!

---

### Post by bruce89 on 2006-05-31
```
sudo aptitude install sun-java5-jre
``` installs java.

---

### Post by user1397 on 2006-05-31
[quote=PriceChild]Those files are java aren't they? that's all in the repos![/quote] [quote=bruce89]```
sudo aptitude install sun-java5-jre
``` installs java.[/quote] This only works in dapper.  Since u04f061 hasn't mentioned yet what version he uses, this info wouldn't be of much help to him.  He might be using breezy, where java is a lot harder to install than in dapper. 
By the way, u04f061, most of the programs you'll ever need in ubuntu will be found in the repositories, that is, you can find them using the search function in this program: Synaptic Package Manger (System->Administartion->Synaptic Package Manager)
Yo could also use the command line for installing programs from the repositories.  For example, to install the program called "foo", you would type in a terminal (applications->accessories->terminal) : ```
sudo apt-get update && sudo apt-get install foo
``` or better yet, use this command (it is far better for installing programs than apt-get, as it remembers dependencies very well: ```
sudo aptitude update && sudo aptitude install foo
```

---

### Post by bruce89 on 2006-05-31
[QUOTE=erik1397]This only works in dapper.  Since u04f061 hasn't mentioned yet what version he uses, this info wouldn't be of much help to him.  He might be using breezy, where java is a lot harder to install than in dapper. 
[/QUOTE]
It would be simple enough to upgrade to Dapper tommorrow.

---

### Post by user1397 on 2006-05-31
[quote=bruce89]It would be simple enough to upgrade to Dapper tommorrow.[/quote] Got me once more, bruce89!!! :mrgreen:

---

### Post by bruce89 on 2006-05-31
[QUOTE=erik1397]Got me once more, bruce89!!! :mrgreen:[/QUOTE]
!

---

### Post by u04f061 on 2006-05-31
thnx to all of u and sad to inform u that i got nothing from your replies.i know how to use apt-get.i was not asking about how to install java(java is not a software itself having an installer.it is a language having much more u think,like jdk is development kit,jre is its runtime environment,javac is its compiler found in jdk,so what is the meaning of installing java?which package to install)

the purpose of this post was to understand how to install these files .

thnx to jagot for giving useful link.

---

