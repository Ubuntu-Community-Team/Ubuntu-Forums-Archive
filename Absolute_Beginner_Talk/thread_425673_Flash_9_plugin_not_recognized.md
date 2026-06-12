---
title: "Flash 9 plugin not recognized"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by apunc1 on 2007-04-27
A few months ago, using the Ubuntu build of Firefox, I updated to Flash 9 using the method described below

> **SimonLoftus said:**
> After reading all of the hugely jumbled up tutorials I got annoyed because non of the stuff seemed to work, or was like a 10 page instruction to do the simplest thing i've seen.

Like my other tutorial for wide screen resolution here is another that is SUPER noob friendly :)

I had a pretty much clean install of ubuntu, except for a few things to do with my monitor resolution.  So this is what is needed to update to flash 9 to use youtube videos that had no sound before.  

It takes 30 secs.

Download this:   [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

Extract it somewhere, desktop is easiest.  

Then open up your terminal, Applications/Accessories/Terminal 

First we have to get you to the folder, assuming it is on the desktop,

Type "cd ~/Desktop"
Then "cd install_flash_player_9_linux"

Type "sudo cp -r libflashplayer.so /usr/lib/firefox/plugins"

Close off all of your firefox browsers and reopen and it will be working perfect :D

You may be wondering why you cant just copy the file into that folder, because that is all the commands do.  This is because the folder is protected, this stops viruses etc I believe.

Hope you all find it super simple, after all it is, cya xx

And it worked perfectly. 

Now I have installed the Mozilla build of Firefox using the method here [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox)

It installed fine. Then I tried to install Flash 9 the same was as before and in the terminal when I tried to excute the 'cd install_flash_player_9_linux" command it would not install.

I checked my plugins with 'about: plugins' in FF v2 and Flash 7 and Flash 9 are listed. Flash 7 is the only one recognized. How do I make Flash 9 recognized? I do not have the Flash 7 from Symantic installed. I am using Dapper.

---

### Post by lamalex on 2007-04-27
have you tried installing using the directions from adobe? try running through the install and see if it works.

---

### Post by apunc1 on 2007-04-27
Yes, I tried it through the Adobe site as well last night to no avail. 
When I entered the install command in terminal (which is different than the method I tried previously) there was a "command not found" error. I copy and paste the commands.

---

### Post by apunc1 on 2007-04-27
well I found what my problem is but I'm not sure how to fix it. I have the problem described here [http://www.digitalramble.com/2007/02/27/95/](http://www.digitalramble.com/2007/02/27/95/)

I located the libflashplayer.so files and renamed the one with the older date, closed down firefox, and still have both Flash 7 and 9 installed, with FF only recognizing 7.

I'm not sure If i'm understanding the article correctly, or if it matters that I have two backups of .mozilla in my home folder (i guess because I unistalled FF2 because I couldn't get Flash working and then reinstalled it? or because I installed the flash plugin multiple times?)

---

### Post by Najand on 2007-04-27
remove flash from apt:
```

sudo apt-get remove flashplayer-mozilla flashplugin-nonfree 

```and then install the newer one from "multiverse"
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by apunc1 on 2007-04-27
when I entered the first command I received this
```

Package flashplayer-mozilla is not installed, so not removed
```

---

### Post by Najand on 2007-04-27
ok.... Do it without that!

---

### Post by apunc1 on 2007-04-27
I installed the non-free plugin and still no change

would simply replacing the old libflashplayer.so with the new one work? or is that too easy? The problem is Firefox is looking in the directory where Flash 7 is first then where flash 9 is.

---

### Post by Najand on 2007-04-27
Can you copy and paste the output of:
```

cat ~/.mozilla/pluginreg.dat

```

---

### Post by apunc1 on 2007-04-27
```
cat: /home/apunc1/.mozilla/pluginreg.dat: No such file or directory
```

---

### Post by Najand on 2007-04-27
Can you "ls" the contents of directory .mozilla in your home?

---

### Post by apunc1 on 2007-04-27
the output of the ls command is

```
firefox  mozver.dat  plugins

```

thanks for your interest and help!

---

### Post by Najand on 2007-04-27
can you tell me if there is a file called "pluginred.dat" in the firefox folder or not? If there is can you copy/paste it here? Also please tell me the location you installed Flashplayer9 .

---

### Post by apunc1 on 2007-04-27
Yes, pluginred.dat is in the firefox folder. the contents of the firefox folder are
```

h9hxozv5.default  pluginreg.dat  profiles.ini
```

Flash 9 is installed in usr/lib/firefox/plugins

---

### Post by Najand on 2007-04-27
I meant can you copy and paste the output of:
```

cat ~/.mozilla/firefox/pluginreg.dat

```

---

### Post by apunc1 on 2007-04-27
same as before: no file or directory found

---

### Post by Najand on 2007-04-27
Sorry, I had forgotten the dot(.) before mozillal. Can you do it again?

---

### Post by apunc1 on 2007-04-27
Generated File. Do not edit.

[HEADER]
Version:0.08:$

[PLUGINS]
/usr/lib/firefox/plugins/libflashplayer.so:$
:$
1177709637000:1:5:$
Shockwave Flash 9.0 r31:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
/home/apunc1/.mozilla/plugins/libflashplayer.so:$
:$
1085078040000:1:15:$
Shockwave Flash 7.0 r25:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

---

### Post by Najand on 2007-04-27
> **apunc1 said:**
> Generated File. Do not edit.

[HEADER]
Version:0.08:$

[PLUGINS]
/usr/lib/firefox/plugins/libflashplayer.so:$
:$
1177709637000:1:5:$
Shockwave Flash 9.0 r31:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
/home/apunc1/.mozilla/plugins/libflashplayer.so:$
:$
1085078040000:1:15:$
Shockwave Flash 7.0 r25:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

OK, Now try to remove the lines:
> /home/apunc1/.mozilla/plugins/libflashplayer.so:$
and
> Shockwave Flash 7.0 r25:$
Save, do "killall firefox-bin" and start firefox again.

---

### Post by apunc1 on 2007-04-27
How do I edit the generated output?

---

### Post by Najand on 2007-04-27
Try
> gedit ~/.mozilla/firefox/pluginreg.dat

---

### Post by apunc1 on 2007-04-27
I was able to edit the file in gedit, save it, then kill firefox. flash 7 is still being recognized above flash 9!

---

### Post by deadgobby on 2007-04-27
[http://ubuntuforums.org/showthread.php?t=279990](http://ubuntuforums.org/showthread.php?t=279990)

---

### Post by Najand on 2007-04-27
Ok, then let us edit that file again:
add the following blue line between the black lines:
```

1174052034000:1:5:$
[COLOR="Blue"]Shockwave Flash 9.0 r31:$[/COLOR]
Shockwave Flash:$


```

---

### Post by Najand on 2007-04-27
shutdown your computer and then check it out.

---

### Post by apunc1 on 2007-04-27
deadgobby,
well i have installed flash 9 now about three different ways about five times and the thread you pointed me to worked! Thanks! I don't know how I missed this thread.

I now have the flash plugin 9 installed **only** and it is functioning properly!

Najand, Thank you for your time and help!

I just wonder why the same method I used to update FF v1.5 didn't work for 2.0

---

### Post by apunc1 on 2007-04-27
> **Najand said:**
> shutdown your computer and then check it out.


hmmm glad I didn't try that, ha

---

### Post by Najand on 2007-04-27
That is something nice to know.
What is the method you used for updateing Firefox?

---

### Post by apunc1 on 2007-04-27
I used the Ubuntuzilla script to upgrade to the official mozilla firefox build

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox)

---

### Post by Najand on 2007-04-28
Well.... I prefer to use the firefox patch made for ubuntu than the one built by mozilla... Maybe you can ask the people who made that homepage.

---

### Post by apunc1 on 2007-04-28
it has a support forum here in 3rd party projects but I wasn't sure the upgrading method was the problem because I had searched here for firefox flash and upgrade problems and hadn't seen anything
the ubuntuzilla page was linked off [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Najand on 2007-04-28
I didn't said there is a problem with that method. I just said I don't have enough information about it.

---

### Post by deadgobby on 2007-04-28
YES! I am glad to help out. That has made my day. :) Cats web site and the other forum post has some conflicts on how to install flash.

---

