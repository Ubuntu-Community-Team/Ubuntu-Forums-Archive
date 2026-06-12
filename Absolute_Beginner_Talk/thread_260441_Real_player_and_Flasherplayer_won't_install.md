---
title: "Real player and Flasherplayer won't install"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Tominator on 2006-09-18
I've got the 6.06 version which I installed from a mailed disk, I have done my updates. I let the system attempt to install both and it failed on both. I attempted to do a manual install on both using the directions provided on the web sites. That didn't work for either. Help will be appreciated.

---

### Post by raul_ on 2006-09-18
They didn't work how? Run apt-get or aptitude again and post the code, or try to install manually and post exactly what didn't work, that way we can help u =)

---

### Post by Dinerty on 2006-09-18
**Originally created by [B]Artifical Intelligence
[/B]
Manually:

Download flash from here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW)
to your Desktop.

Close your browser(s), to the terminal, batman

```
cd Desktop
tar -zxf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
sudo sh flashplayer-installer
```

When you see this:
Quote:
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):

type: **/usr/lib/mozilla-firefox**

Done.

Now you need install the fonts that flash needs:

```
sudo apt-get install gsfonts-x11
sudo fc-cache -f -v
```

Done.



Hope this helps

---

### Post by Tominator on 2006-09-18
Thank you Dinerty, that worked. As to Raul's response, all I get is, ,"no such file or directory" when I follow all instructions. Anybody got a good fix for Realplayer install?

---

### Post by powder on 2006-09-18
> **Dinerty said:**
> **Originally created by [B]Artifical Intelligence
[/B]
When you see this:
Quote:
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):

type: **/usr/lib/mozilla-firefox**


It's better to point the installer to /usr/lib/firefox as /usr/lib/mozilla-firefox is just a symlink to /usr/lib/firefox.  In other words, whatever you put in /usr/lib/firefox will also be in /usr/lib/mozilla-firefox.

---

### Post by Dinerty on 2006-09-19
> **powder said:**
> It's better to point the installer to /usr/lib/firefox as /usr/lib/mozilla-firefox is just a symlink to /usr/lib/firefox.  In other words, whatever you put in /usr/lib/firefox will also be in /usr/lib/mozilla-firefox.

Thanks, will alter the guide to show this :)

---

### Post by Tominator on 2006-09-19
Still struggling with Real install. Can't seem to get to the point where I make the Mozilla-Firefox change. Can someone give me code to install in terminal like Dinerty did for Flash. Thanks all.

---

### Post by mongooseman1128 on 2006-09-19
I know this is a little on a tangent, but I can't help but notice that the command sudo comes up a lot. What exactly does that do? (forgive my ignorance, I've been on windows all my life)

---

### Post by Tominator on 2006-09-19
I don't know much Mongoose but I can tell you that stands for "super user do". A security deal I think.

---

### Post by elementadiobam on 2006-09-19
> **mongooseman1128 said:**
> I know this is a little on a tangent, but I can't help but notice that the command sudo comes up a lot. What exactly does that do? (forgive my ignorance, I've been on windows all my life)

Sudo gives you the root privileges I think. You use it when you are doing something that involves installing or removing a progam or various other administrative tasks.

---

### Post by geovino on 2006-09-20
How do you install the RealPlayer10GOLD.bin?



> **Dinerty said:**
> **Originally created by [B]Artifical Intelligence
[/B]
Manually:

Download flash from here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW)
to your Desktop.

Close your browser(s), to the terminal, batman

```
cd Desktop
tar -zxf install_flash_player_7_linux.tar.gz
cd install_flash_player_7_linux
sudo sh flashplayer-installer
```

When you see this:
Quote:
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):

type: **/usr/lib/mozilla-firefox**

Done.

Now you need install the fonts that flash needs:

```
sudo apt-get install gsfonts-x11
sudo fc-cache -f -v
```

Done.



Hope this helps

---

### Post by Tominator on 2006-09-20
I think I got something that works for Real. I did an update this morning and one of them was for a player plug in. I got an error messsage, restarted amd checked for updates and was informed that I am up to date. Then I went to a site that i had trouble with originally, (NFL.COM) and the whole page loaded with no pop ups saying I needed plugins to view it. So thanks all, I'm off to my next thread to try and get my sound card to work.

---

### Post by mongooseman1128 on 2006-09-21
I was having the same problems installing flashplayer, but when I try to do what geovino said, it errors out and tells me no such directory exists

---

### Post by Tominator on 2006-09-21
What worked for me is that bit dinerty had that geo provided. But i still think the latest updates deal with this issue. Good luck goose.

---

### Post by mongooseman1128 on 2006-09-21
actually, I was toying around with it and came to the realization that terminal is case sensitive so that lower case d in desktop was getting me nowhere fast

---

### Post by Tominator on 2006-09-21
I just started to try to learn something about Linux today. I learned that same thing at Linuxcommand.org. Excellent tool i think.

---

### Post by Dinerty on 2006-09-22
> **geovino said:**
> How do you install the RealPlayer10GOLD.bin?

**Originally created by **Taurus**

```
cd ~/Desktop
chmod 755 RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin (for personal use...)
-or-
sudo ./RealPlayer10GOLD.bin (for system wild...)
```


According to this post, that should work :)

[http://ubuntuforums.org/showthread.php?t=254879&highlight=RealPlayer10GOLD.bin](http://ubuntuforums.org/showthread.php?t=254879&highlight=RealPlayer10GOLD.bin)


Also Real Player 10 is in the repo's, Head to "System > Administration > Synaptic Package Manager > click "Search" then enter "Real Player", version 10 is there :)

---

### Post by Tominator on 2006-09-22
Now ya Got it Dinerty!!! That 1st one came back with an error, so I tried the  2nd one and it worked like a charm. Thanks a million.
Tom

---

### Post by geovino on 2006-10-07
> **geovino said:**
> How do you install the RealPlayer10GOLD.bin?

This is what I get at the terminal:
davek@davek-desktop:~$ cd Desktop
davek@davek-desktop:~/Desktop$ tar -zxf install_flash_player_7_linux.tar.gz
tar: install_flash_player_7_linux.tar.gz: Cannot open: No such file or directorytar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
davek@davek-desktop:~/Desktop$
davek@davek-desktop:~/Desktop$

What am I doing wrong?

---

### Post by Tominator on 2006-10-07
Hello Geo, I don't know what that error message you got means. If you will look at that last post by Dinerty you will see this command,  sudo ./RealPlayer10GOLD.bin (for system wild...), I left off that bit in parenthesis and that is what worked for me. Good luck, Tom.

---

### Post by geovino on 2006-10-07
> **Dinerty said:**
> **Originally created by **Taurus**

```
cd ~/Desktop
chmod 755 RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin (for personal use...)
-or-
sudo ./RealPlayer10GOLD.bin (for system wild...)
```


According to this post, that should work :)

[http://ubuntuforums.org/showthread.php?t=254879&highlight=RealPlayer10GOLD.bin](http://ubuntuforums.org/showthread.php?t=254879&highlight=RealPlayer10GOLD.bin)


Also Real Player 10 is in the repo's, Head to "System > Administration > Synaptic Package Manager > click "Search" then enter "Real Player", version 10 is there :)


I tried to install in synaptic and it said I can't install real player, why?

If its not in synaptic I won't even try to install anymore.

---

### Post by geovino on 2006-10-09
I found Real Player in Synaptic, but when I go to install it says that I can't and displays this:

realplayer:
 Depends: xlibs  but it is not installable

why does this happen?

---

### Post by Merlin 3 on 2006-10-18
But it is not in Dapper :(

---

### Post by xpod on 2006-10-18
Have you added the extra repo`s in dapper...Synaptic>settings>repo`s then click "add" and check the 2 empty boxes?

---

### Post by Merlin 3 on 2006-10-18
Hi Dinerty, Thanks for the instructions for RealPlay ...however when I try to open BBC audio I get this message:Could not find an appropriate realplay in the system path to use as an embedded player..
Any idea what this means and how to correct?

---

### Post by Merlin 3 on 2006-10-18
Found this on BBC website:
The files nphelix.so and nphelix.xpt must be in the browser's plugins directory for Opera, Firefox and Mozilla

Could someone tell me how I do this... I am unexperienced in such affairs!

---

### Post by geovino on 2006-10-24
Thanks I did that, but then I get this error:

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

How do I correct this?

I also get this message when I try to install Real Player:

realplayer:
 Depends: xlibs  but it is not installable 

How do I correct this?

Shouldn't Real Player be installed by default so everybody has it available to them?

---

