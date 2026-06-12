---
title: "[SOLVED] Sound, Flash, and Java"
date: 2007-08-14
forum: Apple PPC Users
---

### Post by thevictor390 on 2007-08-14
OK, I've got a fresh install of Ubuntu on my 500 MHz iBook G3, and now I'm trying to get it into everyday use for my brother.  So, there are 4 separate issues I have not been able to iron out:

1. Mouse set to F11 and F12 (seen plenty of topics on this, not a major concern right now)
2. Sound card not detected at all.  When I go to the control panel on sound it just shows a blank list under devices.  The sound card is the original that came with the computer so I assumed it would be able to pick it up...
3. No Flash support.  From what I can tell, Macromedia does not offer flash for PowerPC linux, so it there anyway I could get that or a third-party app working?
4. No Java.  this is a big concern for him since he wants to play runescape and for me since I am learning to develop myself.  Is there any way to get at least the runtime envoronment running?

Sorry for all of the questions, but I didn't want to make 3 topics.  Thanks in advance.  I am new to linux, so forgive me if a solution seems obvious.

---

### Post by Auria on 2007-08-14
> **thevictor390 said:**
> 
3. No Flash support.  From what I can tell, Macromedia does not offer flash for PowerPC linux, so it there anyway I could get that or a third-party app working?
4. No Java.  this is a big concern for him since he wants to play runescape and for me since I am learning to develop myself.  Is there any way to get at least the runtime envoronment running?


see teh PPC FAQ, it's a sticky, it has these answers and many more - very useful resource

---

### Post by thevictor390 on 2007-08-14
Thanks, I thought I checked that but I must have missed it..

---

### Post by thevictor390 on 2007-08-14
Ugh, this is frustrating...

I remapped to right and middle mouse buttons to the apple key and function+apple key respectively, but F11 and F12 remain mouse buttons.  I commented them out in the config file, however.  Not a big deal, but annoying nonetheless.

I installed Gnash 0.8.0 but it won't run either as a plugin or standalone.  Firefox still reports the flash plugin missing, and when I run from the applications menu nothing happens.

I also tried to install the IBM Jave Runtime Environment 1.5.  The files are all there but again Firefox will not recognize the plugin (and I followed the steps that supposedly fixed this).  I do have a standalone application to test with it, but have not had a chance to do so.

Overall, I'm starting to question whether Linux on PPC is really worth it, although I don't feel like dropping $100+ on for a soon-to-be-obsolete operating system that will barely run, just as OS X 10.5 comes out dropping the G3 lineup.

EDIT: forgot to mention, still no sound.  Any idea why it doesn't even recognise the existance of the hardware? It still makes the "duuuuuuuuuuuuuunhhhh" noise when I boot it up and sound worked in Mac OS X 10.2 (and I think Ubuntu 6.10, not sure).

---

### Post by Auria on 2007-08-15
> **thevictor390 said:**
> 
I installed Gnash 0.8.0 but it won't run either as a plugin or standalone.  Firefox still reports the flash plugin missing, and when I run from the applications menu nothing happens.


check you also installed the browswer plug-ins, usually it's a seperate package

> 
Overall, I'm starting to question whether Linux on PPC is really worth it
i don't have an answer to your sound problem, but if you stay around for some time there a few very knowledgeable people here that may get it sorted.
if you need flash 9 though, linux ppc will not be suitable for you.

---

### Post by thevictor390 on 2007-08-15
OK, gnash is now working as a plugin, I'm going to try to reinstall the Java plugin through Synaptic, which is how I got flash working.  It's not perfect, but it's better than nothing.  Still no sound, too.

EDIT: no luck with Java, either,  All the files for the RE seem to be there, but I can;t run a program that supposedly only requires 1.4 (although the "java" command seemed to be recognized) and I can't find a plugin for Firefox to run applets.  Sorry for all these questions, but I really am lost here.

---

### Post by Sachsa on 2007-08-15
If it's any encouragement to you, i just got ibm java going on a PowerMac G3, under Xubuntu 6.10. I know next to nothing about linux, but here's what i did based on googling around....

added  Medubuntu to the sources.list file and used Synaptic to install the runtime and SDK for Java 1.50.

(Despite messing around with $CLASSPATH etc i haven't got the shell to recognise any Java  commands - it claim's it can't find a certain file, even though i can clearly see it in the file manager)

I got the firefox plugin going by putting a symlink to libjavaplugin_oji.so  in the mozilla-firefox/plugins folder. 

i also ran the Java control panel just by clicking on the file. Call me superstitious, but i think things came to life after that.

good luck 
s

---

### Post by thevictor390 on 2007-08-15
I'm not too worried about terminal commands not working, as the browser plugin is my current goal.  I'm gonna see if I can figure out the syntax to manuall add the plugin to the list like you did...

EDIT: I'm having trouble finding the Firefox program directory, anyone know it's default location?

---

### Post by Sachsa on 2007-08-15
the firefox folder you're after, on my system at least is /usr/lib/mozilla-firefox/plugins

i ran this to set up the symlink (you have to be in the plugins directory at the time):
sudo ln -s /usr/lib/j2sdk1.5-ibm/jre/bin/libjavaplugin_oji.so 

it might be worth checking the path is correct.
cheers
s

---

### Post by thevictor390 on 2007-08-15
Thanks, I found the folder but the link to the Java plugin (which was there) was broken.  I don't appear to have permission to create a link from the original or modify the one there.  also, libjavaglugin oji.so (my hyphen/underscore key is broken) doesn't exist for me, the closest I could find was libjavaplugin ns[six] oji.so (space=underscore, [six]=the number; my six key doesn't work either)...

I'm going to try to use that file...

edit: I'm almost positive this is the problem... it's linking to a file in the j2sdk but I only have the jre... so I tried to create a new link to the file in the jre but I don;t have permission to overwrite the old one, or modify anything in either folder for that matter ("I am not the owner"?!) This is the only account on this computer so I don't see how I could be lacking any administrative rights... so now I can't fix or delete the broken link.

edit again: Got it.  My own stupidity aside (I thought the file didn't exist when it was right there in front of me), the problem was that the original plugin linked to the j2sdk but I only have the j2re installed, so I had to change the link accordingly.  "sudo" fixed the permissions problem.  For anyone else with this issue: navigate to the usr/lib/j2re1.5-ibm/jre/bin

sudo rm libjavaplugin_oji.so
sudo ln -s /usr/lib/j2re1.5-ibm/jre/bin/libjavaplugin_oji.so

basically, remove the old link and change sdk to re.

Thanks for your help Sachsa.

So, now it is only sound that does not work.  Any ideas?  This and the mouse buttons still mapped to F11 and F12 are now my only issues with Ubuntu.

---

### Post by Sachsa on 2007-08-15
i don't think you have root admin rights on ubuntu even if you are the sole user, and tht file is probably owned by root (ls -la will tell you) The sudo command should grant you rights temporarily though, as long as your name's in the sudoer's file.
by the way i tried that ns6 file, and it didn't work.

missed that last update....glad you got it going
s

---

### Post by thevictor390 on 2007-08-15
Thanks again, still looking to unmap F11 and F12 and get sound working.

Also, since the 6 and - keys don't work (I'm on another comp now), is there a way I could set F11 and F12 to those?

---

### Post by BryannMelvin on 2007-08-17
OK I'm running Feisty on a G3 500 dual usb ibook
IBM Java works for somethings not for others,

Following the stickied FAQ  instructions fixes some things not others for Java
Many Java programs are X86 ONLY despite being Java! foolish yes but....

Looking at errors I find that Juploader (for Flickr) and Jalbum  don';t work. one or both showed errors relating to x86 stuff not being available.

To get *.JNL stuff working I needed to create a file association.
 Not ALL java web apps will work with IBM Java anyway. an example of this is Thinkfree Office
for some applets I have found it useful to download the copy and then run it.

Once you THINK you might have Java set up...Go to Sun's test site. If the Java is working you'll get told you have an old version etc etc but the little cartoon character will still dance.

If that works ....then the app just isn';t going to work.
Note that you need to change the default Java to IBM from the FOSS version

ALSO some Java apps will only look in the environment variables for Java and go no further.
This isn't set in any version of Ubuntu I have used. 


F11 and F12 are set up as the mouse buttons by a kernel module. You will need to remove that module to stop them from working I believe. ...something about Mouse button emualtion module not sure it's been a while since I compiled a ppc kernel,.


Gnash works OK for ads  doesn't help for most News videos etc, I have gotten some working but not many and the VLC AND Gstreamer etc seem to make the system unstable I have clicked on news videos a few times and ended up back at the Login screen with Gnoem or KDE crashing.

Lastly ( but not mentioned by you ) forget the modem...it IS a hardware modem but I haven't  gotten it working on Ubuntu since 5.04! 

I just carry around an old 5.04 live cd in case I have to use the modem  when on the road,

---

### Post by BryannMelvin on 2007-08-17
addendum

I had to add the sound modules to /etc/modules to get sound working on the ibook

---

### Post by thevictor390 on 2007-08-17
Don't worry, I don't plan on using any internet connection besides wireless (which works great out-of-the-box).  I have Java working well enough, as I have not found anything that won't work yet, and I understand that Flash is WIP (yes, it crashes a lot for me too).

Now, you say add the module to get sound? Sorry if I should know this, but how exactly do I do that?

---

### Post by BryannMelvin on 2007-08-19
I had to add snd-powermac:

gksudo (or sudo from a a terminal) gedit /etc/modules
or
kdesu kate /etc/modules

(or your favourite editor as root)

add a line:

snd-powermac

save it and the sound card should be recognized on the next boot

---

### Post by thevictor390 on 2007-08-19
Worked like a charm, on both models of iBook!  Thanks for a simple fix! Odd that this isn't loaded by default.

---

