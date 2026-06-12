---
title: "Any messenger with webcam support?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by vicisgoodtogo on 2007-08-13
Hello! I'm a TOTAL newbiee! Just installed Ubuntu!
I got skype and GAIM working lol... But that's easy huh? It's all microsoft easy way...
But... I wanna use a program with webcam support. I read that aMSN is the one... But I have no idea how to install it... Is there any other program or that is the only way? If so... How do I install it?
I'm running version 7.04 Ubuntu.
Thx a lottt.

---

### Post by amazingtaters on 2007-08-13
aMSN can be gotten via the Add/Remove Programs feature in applications on your toolbar. It's very easy, all gui phun.

---

### Post by vicisgoodtogo on 2007-08-13
omg...

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

what happened? xD
whast do i do?

---

### Post by Cable on 2007-08-13
Hey there.  To install aMSN, simply go to Applications>Add/Remove.  Then be sure that the "Show" menu has "All available applications" selected.  Then just type amsn in the search box, check the box next to the aMSN result, and click ok.  You should be good to go.  :-)

---

### Post by vicisgoodtogo on 2007-08-13
Thx guys, but it seems i can't acess that anymore...
=/
vic@vic-desktop:~$ sudo apt-get update
Password:
E: Type '“deb' is not known on line 44 in source list /etc/apt/sources.list

---

### Post by snkiz on 2007-08-13
> **vicisgoodtogo said:**
> omg...

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

what happened? xD
whast do i do?

do exactly what it says synapitic can be found in system preferences and the sudo stuff you enter from a terminal those commands work I've used them

---

### Post by vicisgoodtogo on 2007-08-13
how do i do all that? :(

i went to synaptic package manager and it said
E: Type '“deb' is not known on line 44 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by amazingtaters on 2007-08-13
Open up your terminal Apps->Accesories->Terminal and type in the commands it gave you,  sudo apt-get update  and then  sudo apt-get install -f

---

### Post by sstusick on 2007-08-13
Skype doesn't have webcam support? I thought that was one of Skype's strong points.

---

### Post by vicisgoodtogo on 2007-08-13
i did it
this is what happens

vic@vic-desktop:~$ sudo apt-get update
E: Type '“deb' is not known on line 44 in source list /etc/apt/sources.list
vic@vic-desktop:~$

:(

---

### Post by vicisgoodtogo on 2007-08-13
what do i do? :(

---

### Post by meierfra on 2007-08-13
somehow the file /etc/apt/sources.list got messed up.

Please post the output of

```
cat /etc/apt/sources.list
```

---

### Post by amazingtaters on 2007-08-13
Post up your sources.list plz so we can have a look at line 44

---

### Post by vicisgoodtogo on 2007-08-13
it said invalid type of file
=/


but here is what it said


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

---

### Post by vicisgoodtogo on 2007-08-13
it seems to be the last stuff right? should i just erase it?

i mean the last block
i was trying to install automatix to install amsn

---

### Post by amazingtaters on 2007-08-13
ahh your problem is the quotes around two of the entries, the automatix ones. I believe that fixing those should set you on the right track

---

### Post by meierfra on 2007-08-13
Delete the last five  lines  (except the very last one if you want to keep automatix uptodate)

---

### Post by vicisgoodtogo on 2007-08-13
what should i do exactly?
i'm the most noob person around...

---

### Post by amazingtaters on 2007-08-13
> **meierfra said:**
> Delete the last five  lines  (except the very last one if you want to keep automatix uptodate)

Do what he said...

---

### Post by vicisgoodtogo on 2007-08-13
lemme try! :D

---

### Post by meierfra on 2007-08-13
open the file via

```
sudo gedit /etc/apt/sources.list
```

Delete the lines I said and save the file

---

### Post by vicisgoodtogo on 2007-08-13
it says i don't have permission to save the file over itself! xD

---

### Post by amazingtaters on 2007-08-13
did you open it via sudo? workaround that I have used (not a good way, and someone will tell you not to do it probably) but I have saved an updated version of a file that needed root permission to edit to my desktop, then used "sudo mv filename path" to overwrite the old version.

---

### Post by vicisgoodtogo on 2007-08-13
k let's see

---

### Post by vicisgoodtogo on 2007-08-13
duuuuude
hahaha
that was great!!!
thanks!

---

### Post by vicisgoodtogo on 2007-08-13
now i did via sudo!
great!
idk if i'm gonna remember all that though hehe.

---

### Post by amazingtaters on 2007-08-13
got it to work then? bookmark the page, its what I do all the time.

---

### Post by vicisgoodtogo on 2007-08-13
still can't find aMSN though hehe. looking for it on add/remove.

---

### Post by amazingtaters on 2007-08-13
cut it down to internet applications and that will help you wade through all the stuff

---

### Post by vicisgoodtogo on 2007-08-13
found!
great!
downloading!
:)
next part will be confign!^^ thanks a lot again!

---

### Post by bwtranch on 2007-08-13
# deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
 NO! You are getting some bad info here:(

It says uncomment the following two lines. That means take out the # in front of these two and save it.:)

---

### Post by vicisgoodtogo on 2007-08-13
ok, installed aMSN.
but when logging in it says error installing TLS module... Ubuntu 7.04x86 is linux x86 right?

---

### Post by amazingtaters on 2007-08-13
yeah

---

### Post by vicisgoodtogo on 2007-08-13
it says... downloaded... but then...
aMSN error!
error installing tls module:couldn't get http:/switch.dl.sourceforfe.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz

---

### Post by snkiz on 2007-08-13
automatrix is unsupported and can cause problems espicaly if you upgrade try mediubuntu insted

---

### Post by vicisgoodtogo on 2007-08-13
no need for automatix anymore.
but can't get amsn to work. =/

---

### Post by snkiz on 2007-08-13
I'm no expert but i could be a bad download wipe it out and try again it worked for me in the past

---

### Post by vicisgoodtogo on 2007-08-13
should i try getting TLS separated?
bc amsn downloads that and accuses an error.

---

### Post by bwtranch on 2007-08-13
First of all. I would be afraid of installing anything on a Linux system that had a name like MSN. You need to back up a little and do things right or you are going to mess up your system. Windows doesn't run very well because everything is haphazard. I do some crazy stuff sometimes, but I am a testing user and have a backup computer. We can't just start putting things in different folders (directories) and expect them to work properly. File structure is very important in this arch and you can't learn it in a day. I am no guru either and I learn something every day. But, this is the first lesson.

---

### Post by vicisgoodtogo on 2007-08-13
dude...
i agree.
i'm not filling up my HD.
and you didn't really answer my question.
what i want is to make this aMSN work. if you can help me, that'd be great.

---

### Post by meierfra on 2007-08-13
I suggest to reinstall via add/remove  (maybe you just had a bad internet connection)

---

### Post by vicisgoodtogo on 2007-08-13
ok i'll do that.
but that's be weird with a 2mb connection.
but i will try. :)

---

### Post by vicisgoodtogo on 2007-08-13
uninstalled and installed again.
same error.
the problem is the TLS.

---

### Post by meierfra on 2007-08-13
> error installing tls module:couldn't get http:/switch.dl.sourceforfe.net/sourceforge/amsn/t ls-1.5.0-linux-x86.tar.gz

This sounds like you  are having  problems connecting to some server. 
 
In add/remove click on preferences. Under "download from" pick a different server and try again

---

### Post by vicisgoodtogo on 2007-08-13
wasn't that either.
=/

---

### Post by meierfra on 2007-08-13
Sorry I think I misunderstood your problem. I  thought your error occured  while  installing amsn.

But now I think that you installed amsn without an error message. Is that right?

next you started amsn and tried to log into msn?  When exactly did you get the error message?

I probably won't  be able to help you  anymore, since I don't know anything about amsn. But at least I'm  bumping your thread.

---

### Post by meierfra on 2007-08-13
I just found this link:

[http://www.getautomatix.com/forum/index.php?showtopic=1182&st=0]("http://www.getautomatix.com/forum/index.php?showtopic=1182&st=0")


It seems people had the same problem and solved it.

---

### Post by vicisgoodtogo on 2007-08-13
thanks i'm gonna take a look

---

### Post by vicisgoodtogo on 2007-08-13
great! :D

---

### Post by Vic! on 2007-09-05
aMsn is awesome i got it im also a newbie and i think its great. i even installed it on my mac also. let me know how u like it if u get it

gluk 

V

---

### Post by Pikestaff on 2007-09-12
> **meierfra said:**
> I just found this link:

[http://www.getautomatix.com/forum/index.php?showtopic=1182&st=0]("http://www.getautomatix.com/forum/index.php?showtopic=1182&st=0")


It seems people had the same problem and solved it.


This link fixed my aMSN problems as well, thank you! :)

(Note: if it still doesn't work, notice post #27 in that thread... that's how it worked for me.)

---

