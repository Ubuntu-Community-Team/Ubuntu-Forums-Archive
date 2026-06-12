---
title: "Upgrade Help"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by KIFIKA on 2007-01-12
I really want to upagrade to the latest version of Ubuntu. Currently i an using 5.10 breazy badger. I have spent the better part of today on google looking for instruction on how to do it, but everything i try i run into an error. 

I can't download and burn the iso, because i dont have a cd burner.

---

### Post by rai4shu2 on 2007-01-12
You can order Dapper through shipit, or if you're willing to spend about $5 you can order Edgy from a commercial distro like osdisc.com.

---

### Post by Modernity on 2007-01-12
what kind of errors are you running into? Are you trying to edit your sourceslist? I don't remember about 5.10, so you will have to work with me alittle to help you out.

-Give us the errors you are having and how you are going about in up-grading.

---

### Post by KIFIKA on 2007-01-12
Uhm the errors i was running into depended on what method i tried to use; if you give me a way to try, ill tell you what happens. 

Or do you want me to find all the tutorials, try them again and post each error? 

thanks, 

KIFIKA

---

### Post by Modernity on 2007-01-12
Have you tried doing this yet?

[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-upgrading-ubuntu.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-upgrading-ubuntu.html)

---

### Post by KIFIKA on 2007-01-12
Hey, thanks I just need to make sure i'm doing it right - or am on a right track. 

I went to that link you gave me but i didnt like the warning it gave me so i was a bit creeped out. 
I read what it was going to do, so instead of replacing it with the code it gave i went to 

ubuntu-nl.org/source-o-matic/ 

and finished with the set up, when i restart i ran synaptic package manager and got an error about how there were too manythings to install and that i need to run smart synaptic manager or something along those lines. I pressed okay and install 

and here is what it looks like so far, 

[http://img391.imageshack.us/img391/6733/screenshotnx1.png](http://img391.imageshack.us/img391/6733/screenshotnx1.png)

tell me if im on the right track please?

---

### Post by Modernity on 2007-01-12
It looks like you are on your way, but I would close some of those processes you have running, it might help speed up the process, ie Buddy list. I am not sure what else you are running so, be patient. By the way, you did a back-up right?

---

### Post by KIFIKA on 2007-01-12
Nope, but i'ts okay because there is nothing i'm really worried about loosing; if i did mess up i would just waste my night re-installing a new copy of ubuntu.... 

i have nothing better to do tonight, im kinda bored actually...

---

### Post by Modernity on 2007-01-12
LOL, well, good luck on your up-grade. Let us know how it goes.

---

### Post by KIFIKA on 2007-01-12
ugh, okay well after that finished i got:

[http://img151.imageshack.us/img151/9172/screenshot1jh4.png](http://img151.imageshack.us/img151/9172/screenshot1jh4.png)

what should i do now? I tried "apt-get dist-upgrade" but i received 
"E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
"

---

### Post by rai4shu2 on 2007-01-12
You need to close the updater, then try the apt-get dist-upgrade again.

---

### Post by KIFIKA on 2007-01-12
> E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


is the error i got. Also, i noticed all my icons changed.

---

### Post by rai4shu2 on 2007-01-12
You need to close every other installer program before using that command. That's why you get that error.

---

### Post by KIFIKA on 2007-01-12
as far as i know every other installer program is closed 

[http://img412.imageshack.us/img412/4998/screenshotft0.png](http://img412.imageshack.us/img412/4998/screenshotft0.png)

---

### Post by rai4shu2 on 2007-01-12
I see what happened. You need to do this:

sudo apt-get dist-upgrade

---

### Post by KIFIKA on 2007-01-12
> nick@ubuntu:~$ sudo apt-get dist-upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


is what i get afterwards

---

### Post by rai4shu2 on 2007-01-12
Try this one:

sudo fuser /var/lib/dpkg/lock

---

### Post by KIFIKA on 2007-01-12
okay, i restarted my computer and tried the first one again and i got 
> nick@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  initramfs-tools: Depends: volumeid but it is not installed
E: Unmet dependencies. Try using -f
.
nick@ubuntu:~$ apt-get -f install
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
nick@ubuntu:~$


when i tried the second one:

> nick@ubuntu:~$ sudo fuser /var/lib/dpkg/lock
nick@ubuntu:~$


nothing happened.

---

### Post by rai4shu2 on 2007-01-12
sudo apt-get -f install

---

### Post by KIFIKA on 2007-01-12
okay, it seemed to work.. it downloaded, unpacked, asked me if i wanted to extract y/n i said yes and then it continued, but then i got 

> dpkg: error processing /var/cache/apt/archives/volumeid_093-0ubuntu18_i386.deb (--unpack):
 trying to overwrite `/sbin/vol_id', which is also in package udev
Errors were encountered while processing:
 /var/cache/apt/archives/volumeid_093-0ubuntu18_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


:(

---

### Post by rai4shu2 on 2007-01-13
Almost there. :)

sudo rm /sbin/vol_id
sudo apt-get -f install

---

### Post by KIFIKA on 2007-01-13
thanks for your help and quick replies guys, got an error again :(

> Need to get 0B/54.6MB of archives.
After unpacking 205MB disk space will be freed.
Do you want to continue [Y/n]? y
Abort.


also, my internet is slow atm, is that normal?

---

### Post by rai4shu2 on 2007-01-13
Slowness is caused by many different things, so it's probably normal.

---

### Post by KIFIKA on 2007-01-13
okay, so what do i do now?

---

### Post by rai4shu2 on 2007-01-13
What error are you getting?

---

### Post by KIFIKA on 2007-01-13
It did some more packaging and unpackagin stuff, and so on and so forth..then

>  Need to get 0B/54.6MB of archives.
After unpacking 205MB disk space will be freed.
Do you want to continue [Y/n]? y
Abort.

although, im not sure if its an error or not. But weather it is or not, what do i do next?

---

### Post by KIFIKA on 2007-01-13
[ sorry for this post my internet skipped and i had to reload, i wasnt sure on how to delete the post...lol, sad]

---

### Post by rai4shu2 on 2007-01-13
Looks normal to me. It may take a few minutes to do all that, though.

---

### Post by KIFIKA on 2007-01-13
well, after that nothing happneed.. should i reboot my system?

---

### Post by rai4shu2 on 2007-01-13
As long as it finished all the Setting up stuff, you should be okay to reboot.

---

### Post by KIFIKA on 2007-01-13
sorry i missed a second of that error

>   xfonts-scalable xfonts-utils xkeyboard-config xterm
66 upgraded, 73 newly installed, 130 to remove and 513 not upgraded.
14 not fully installed or removed.
Need to get 0B/54.6MB of archives.
After unpacking 205MB disk space will be freed.
Do you want to continue [Y/n]?
abort.
nick@ubuntu:~$


still think i'm all set to go?

---

### Post by rai4shu2 on 2007-01-13
...

Okay, I'm stumped. Why does it abort there?

---

### Post by KIFIKA on 2007-01-13
ugh, when i restarted it compleatly messed up and wouldnt load right. I installed a new copy, and now i dare to ask the question again:

Should i update my breazy badger 5.10?
and 
How do i update my Breazy Badger Ubuntu 5.10 to a new release of Ubuntu?

---

