---
title: "Google Video and Youtube"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by Daghita on 2006-11-19
So, I did a fresh install of 6.10 of Ubuntu. Went to Google Video or Youtube and Firefox 2.0 completely closes out. I tried installing the Flashplayer 9 by moving it to the plugin folder of Firefox, still does the same thing.

Now, granted I'm not the smartest when it comes to Linux being a beginner. And, I've learned a lot trying to figure this out...not to mention the ka-billion ways to install something. 

But, in my frustration of trying to find information to fix this problem I've been swamped with different information. So, I'm writing this out of a small bit of frustration because I know I'm doing something wrong and I hate not being able to fix it myself.

Is there something that I'm missing that needs to be installed along with the flash player? Because when I go to either site and try playing a video from there, Firefox just closes out completely.

Forgive me if I haven't provided any other information about the system...remember that I'm still new. ](*,)

---

### Post by r4ik on 2006-11-19
Could be wrong here but have you tried,copy and paste,

sudo aptitude purge flashplugin-nonfree flashplayer-mozilla && mkdir /tmp/flash9 && cd /tmp/flash9 && wget [http://www.adobe.com/go/fp9_update_b1_installer_linuxplugin](http://www.adobe.com/go/fp9_update_b1_installer_linuxplugin) && tar zxvf *.tar.gz && rm -rf *.tar.gz && cd * && sudo cp *.so /usr/lib/mozilla-firefox/plugins/

In a terminal ?

Good luck !

---

### Post by Daghita on 2006-11-19
Am I placing the files in a specific area? Am I logging into root in order to run these commands from the terminal?

---

### Post by r4ik on 2006-11-20
Please give this a read,

[https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3](https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3)

Think you need the i386 plugin.

Little late had to sleep :)

---

### Post by nyinge on 2006-11-20
Ok.  Here's the easiest way to get the latest (beta) flash working with firefox.

Go to:
[http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

Download the installer.  NOT the stand alone player.

Open up the compressed file.  You'll see a file, "libflashplayer.so".  Put that in /home/USERNAME/.mozzilla/plugins   ...  Note that you'll need to create the folder "plugins" if that doesn't exist.

Restart Firefox, and...  it should work with flash sites.  First, try going to a flash site like, adobe.com.  Then to google video/youtube.  See if Firefox still crashes.  If not, we're cool, otherwise we're screwed :D.

---

### Post by Portable_Jim on 2006-11-20
[quote=r4ik]     Could be wrong here but have you tried,copy and paste,

sudo aptitude purge flashplugin-nonfree flashplayer-mozilla && mkdir /tmp/flash9 && cd /tmp/flash9 && wget [http://www.adobe.com/go/fp9_update_b...er_linuxplugin]("http://www.adobe.com/go/fp9_update_b1_installer_linuxplugin") && tar zxvf *.tar.gz && rm -rf *.tar.gz && cd * && sudo cp *.so /usr/lib/mozilla-firefox/plugins/[/quote]
How big is the download?

---

### Post by nyinge on 2006-11-20
> **Portable_Jim said:**
> How big is the download?

About 2.48 MB.

2,609,188 bytes to be exact.

Name:  FP9_plugin_beta_101806.tar.gz
md5sum:  0b234c5d0eaf254ef8af364fb9ed97f2
sha1:  fb8ad8ed5ed12c47e1840de1504f5644db08ad29

---

### Post by tommcd on 2006-11-20
here is how I got flsh 9 working. Install flash 7 (flashplugin-nonfree) from synaptic (system>administration>synaptic, you will need multiverse repos enabled under settings>repositories). I have always been able to watch google and youtube vids with flash7. If you want flash 9 then backup libflashplayer.so in /usr/lib/firefox/plugins and cp the libflashplayer.so from the flash9 installer others have linked to to /usr/lib/firefox/plugins.
 Then edit the end of .mozilla/pluginreg.dat to read flash 9 instead of flash 7 (using gksudo gedit). This allowed me to install flash 9 while easily backing up flash 7.
Hope this helps. You can easily move and rename the libflashplayer.so files using ALT+F2, then 'gksudo nautilus' in terminal if you are not comfortable with the command line.

---

### Post by Daghita on 2006-11-20
> **r4ik said:**
> Please give this a read,

[https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3](https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3)

Think you need the i386 plugin.

Little late had to sleep :)

Thank you everyone! It now plays. I followed the instructions on that link you provided (which is basically what you told me to do before) and it worked.

Now that the situation is over, I can continue putting the shaft to other more well known operating systems, by not using their product! Thank you! Time for more learning! :-D

---

### Post by r4ik on 2006-11-21
Glad it works.
Thanks for the reply.

---

