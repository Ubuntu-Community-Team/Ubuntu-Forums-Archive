---
title: "Google Earth - No Earth - No Error"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by imnotryan on 2008-04-17
Installed fine.  No error is displayed.  No mention of a similar problem here or on google.com.

Just no Earth ever gets displayed.  The stars move though.  I'm hoping the inability to select any options (all being grayed out) is a clue.

[IMG]http://i70.photobucket.com/albums/i89/281quadcam/Screenshot-1.png[/IMG]

---

### Post by Tatty on 2008-04-17
try running it from a terminal to see if any error messages are displayed

---

### Post by imnotryan on 2008-04-17
I should probably add that I am using Hardy Heron and have an 8800GT.  I have Compiz and I am enjoying blazingly fast 3d performance with compiz and with TF2 and Garry's mod under WINE.

---

### Post by spiderbatdad on 2008-04-17
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by sharks on 2008-04-17
Try Google Earth without Compiz.

---

### Post by ubukool on 2008-04-17
I've got the same problem on Gutsy.  I've tried running it without compiz but it doesn't seem to make any difference.

---

### Post by imnotryan on 2008-04-17
> **ubukool said:**
> I've got the same problem on Gutsy.  I've tried running it without compiz but it doesn't seem to make any difference.

Doesn't work with or without compiz. :confused:

---

### Post by Tomatz on 2008-04-17
Flash earth:

[http://www.flashearth.com/](http://www.flashearth.com/)

---

### Post by fparri on 2008-04-17
Try launching it as root :)

---

### Post by mutzinet on 2008-04-17
Same problem here.

I am running Kubuntu Hardy with KDE4 and the latest google earth 4.3 with an old ati card. 
I tried to install it in my home directory, in /opt/google-earth, to run it as root, in a terminal, and... nothing :confused: No error message in the terminal and the same symptoms: no earth and most of the options in the menus faded out. 
It looks to me like a connexion problem with the server, but my internet connexion and/or settings haven't changed and it used to work with older GE versions.

After leaving GE opened with no earth for a while, though, I do get an error box saying:

```
Google Earth detected an error while trying to authenticate Please check the following:
- your network connection (can you get to www.google.com?)
- your firewall settings
(are you bloccking /home/*****/google-earth/googleearth-bin?)

Error code: 29
For more information, visit: 
```

And the box shows an "OK" button but no link to visit for more information ;)

---

### Post by Triggerhapp on 2008-04-17
Who blew up Earth? :confused:

---

### Post by agibby5 on 2008-04-17
> **spiderbatdad said:**
> [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

Worked perfectly! :) Thanks!

---

### Post by mutzinet on 2008-04-18
> **agibby5 said:**
> Worked perfectly! :) Thanks!

Did you have the same problem as described before? Because this how-to is the way I did it at first and I do not have any earth in my "Google-no-earth".

---

### Post by ofb on 2008-04-18
Problems with 4.3 may be related to this,
[http://groups.google.com/group/earth-linux/browse_thread/thread/e77715780fd5ede5](http://groups.google.com/group/earth-linux/browse_thread/thread/e77715780fd5ede5)

> I thought you guys deserved an update. The long and short of it is 
that Google Earth 4.3 only works in Linux on machines with processors 
that support SSE2. This means a P4, A64, or greater is now required.

---

### Post by sefs on 2008-04-18
cat /pro/cpuinfo gives

```

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 44
model name      : AMD Sempron(tm) Processor 2800+
stepping        : 2
cpu MHz         : 1600.008
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm ts ttp tm stc
bogomips        : 3203.51
clflush size    : 64

```

its a 64bit sempron and it looks like it supports sse2

Yet I am having the same problem... 
1) No earth
2) Font size is too small to be read.

Any ideas how to fix this...i followed the guide posted earlier in this thread.

Strange enough it works with other accounts BUT NOT main ubuntu account

Why is that?

With ubuntu main account i get only stars in background (places or layers do not load either).. with other accounts  it seems to load fine

---

### Post by mzilhao on 2008-04-20
was having the same problem.
fixed it by removing the Google directory on my .config folder (you may need to be root).

---

### Post by mutzinet on 2008-04-20
Suppressing ~/.config/Google doesn't bring my Earth back. :(

---

### Post by Fedz on 2008-04-20
> **Tomatz said:**
> Flash earth:

[http://www.flashearth.com/](http://www.flashearth.com/)

Easier on the system than running the actual software on your local machine ;)

---

### Post by mutzinet on 2008-04-23
Fixed it!

I followed the steps described here (post from uli.loewe):
[http://groups.google.com/group/earth-linux/browse_thread/thread/91b13b9c3a1ed061#](http://groups.google.com/group/earth-linux/browse_thread/thread/91b13b9c3a1ed061#)

Completely removing googleearth and the directories, reinstalling, NOT starting as root, and now the connection works and my Earth is back.

---

### Post by echris1 on 2008-05-11
> **mutzinet said:**
> Fixed it!

I followed the steps described here (post from uli.loewe):
[http://groups.google.com/group/earth-linux/browse_thread/thread/91b13b9c3a1ed061#](http://groups.google.com/group/earth-linux/browse_thread/thread/91b13b9c3a1ed061#)

Completely removing googleearth and the directories, reinstalling, NOT starting as root, and now the connection works and my Earth is back.

This worked for me too, thanks a lot!

---

### Post by fastfret79 on 2008-05-12
I was having the same problem too - no earth and no error!

Just open a terminal and enter the following:

sudo rm /home/*youruser*/.config/Google/GoogleEarthPlus.conf
sudo rmdir /home/*youruser*/.config/Google

Open up google earth and all is fine!

---

### Post by unc0nn3ct3d on 2008-06-12
> **mzilhao said:**
> was having the same problem.
fixed it by removing the Google directory on my .config folder (you may need to be root).

Thanks for the tip, removing the config/Google dir completely fixed my problem too.. Was driving me batty

---

### Post by mutzinet on 2008-07-06
This problem is far from being fixed for me. :(

Yesterday, wanted to look up something, Google-Earth worked like a charm (except flickering, but that's another issue).

Tonight, I want to have a look again, no earth.
I really don't understand what the problem could be. I'm sitting at the exact same place, with the same network connection, but tonight googleearth doesn't want to connect to the server. :(

---

