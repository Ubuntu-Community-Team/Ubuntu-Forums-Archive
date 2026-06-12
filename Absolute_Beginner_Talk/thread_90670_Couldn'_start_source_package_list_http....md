---
title: "Couldn' start source package list http://..."
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by xyz on 2005-11-15
hi everyone,
i've roamed the site (and other sites) but it's so far always come down to the same  old phrases (on the monitor) following upgrade to breezy thru synaptic:
*couldn't start source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/universe packages...and so on with about half a dozen of the same "couldn't start..." + xserver-xorg is broken or partially installed*

i boot,everything checks [ ok ] and then this on the screen:
*I cannot start the X server(your graphical interface).It's likely that it's not set up correctly.Would you like to view the X server output to diagnose the problem? YES - then: I will disable this X server for now.Restart GDM when it's configured correctly OK*

here are a few things i'v read and tried to apply to solve the problem:

**1.**sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
            sudo gedit (or vim) /etc/apt/sources.list

**2.**sudo perl -pi.bak -e 's|hoary|breezy|g' /etc/apt/sources.list
            sudo perl -pi -e 's|deb cdrom|\# deb cdrom|g' /etc/apt/sources.list
            sudo apt-get update
            sudo apt-get dist-upgrade
              "      "     "   ubuntu-desktop
              "      "     "   update-all

**3.**sudo apt-get install ubuntu-desktop

**4.**in recovery mode (root):
            sudo dpkg-reconfigure xserver-xorg
            apt-get install --reinstall xfonts-base
            followed by:
            /etc/init.d/gdm restart

**5.**sudo vim /etc/apt/sources.list
            replace with:

## Major bug fix updates produced after the final release of the
## distribution...(this is very long to type but i'm sure you get my drift.)

thank you for your help.i'm totally lost and hardly have the knowledge to explain this more clearly.

---

### Post by blueplazma on 2005-11-15
If you don't need the backports source, I'd recommend commenting it out. The other possibility is that your network isn't working. Can you post the entire output of an apt-get update from the command line?

As to your problem with X, can you post the output from the X server when you do startx from the command line? It is difficult to identify your problem without the exact error.

---

### Post by c_riggan on 2005-11-15
I am having this exact same problem.  Would love to know what it is, or how to fix it.

---

### Post by c_riggan on 2005-11-15
Here is what I got when typing startx in the command line:



(==) Log file: "/var/log/Xorg.0.log"
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.0" No
symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.0"  No
symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.0"  No symbols found

(WW) ****INVALID MEM ALLOCATION**** b:0xfff80000 e:0xffffffff  correcting
(EE) I810(0): Cannot read V_BIOS
(EE) I810(0): VBE initialization failed
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
No screens found

XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0"
       after 0 requests (0 known processed) with 0 events remaining




I hope the original poster got the same output, would save them from writing this also.

Thanks for any help I may get here.

---

### Post by xyz on 2005-11-15
nice of you c_riggan to think of me and my fingers but it is not the same output.that would've been cool either way!
**startx**
[I]xauth: creating new authority file  /root/ .serverauth 6869
X: warning; process set to priority -1 instead of requested priority 0 giving up
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error[/I]
**apt-get update**
i'll post here what's on my monitor.Lines went by real fast but as far as i could tell,all other updates seemed to have 'reached target'.

[I]orts/restricted/binary-i386/Packages.gz 404 Not found
Reading package lists...Done.

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirror.net_dists_breezy-backports_main_binary-i386_Packages) - Stat (2 No files....of this type)

W: exactly the same lines here except that "main" is universe.

W: multiverse instead of "universe"

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/restricted Packages (/var.....breezy-backports_restricted_binary-i386_Packages

W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy-updates/main Packages (/var/lib/apt/lists/kubuntu.org_breezy-kde 342_dists_breezy-updates_main_binary-i386_Packages) - Stat (No files....of this type)

W: you may want to tun apt-get update to correct these problems.

E: The downloading of some index files failed, they were ignored or old ones were used instead.[/I]

Blueplazma asked for "_the **entire** output of an apt-get update from the command line?"_As i wrote above,other updated seemed to have 'reached';however, if i must post the entire thing,how do i scroll all the way up?
I don't know if i really need the backports source nor what they are used for,obviously!:confused:
Hope this clarifies things a bit.thanks again!

---

### Post by aysiu on 2005-11-15
Mirrormax is no longer around.
See my sig.

---

### Post by kruz on 2005-11-15
sudo gedit your source list here

make sure when you save
save as then overwrite ur file after 
taking away the # marks

because gedit when you hit the lil save icon
it sometimes saves ur file to 
source.list~
ive noticed this after time after time lol
just an idea if it wont work
then yes
sudo apt-get update

hope this helps a lil

---

### Post by wadesmart on 2005-11-15
11152005 1830 GMT-5

I didnt have any trouble getting mirrormax. Here is the post from my update:
```

wadesmart@wadesmart:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [19.6kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [11.3kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
  404 Not Found [IP: 82.211.81.182 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
  404 Not Found [IP: 82.211.81.182 80]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
Fetched 51.1kB in 5s (9592B/s)
Failed to fetch [http://archive.ubuntu.com/ubunutu/dists/breezy/multiverse/binary-i386/Packa](http://archive.ubuntu.com/ubunutu/dists/breezy/multiverse/binary-i386/Packa) ges.gz  404 Not Found [IP: 82.211.81.182 80]
Failed to fetch [http://archive.ubuntu.com/ubunutu/dists/breezy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubunutu/dists/breezy/multiverse/source/Sources.gz)   404 Not Found [IP: 82.211.81.182 80]
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages ( /var/lib/apt/lists/archive.ubuntu.com_ubunutu_dists_breezy_multiverse_binary-i386_Packages)  - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
Wade

---

### Post by aysiu on 2005-11-15
[QUOTE=wadesmart]11152005 1830 GMT-5

I didnt have any trouble getting mirrormax[/quote] You're having trouble, though. If you follow the instructions in my sig, you won't.

---

### Post by xyz on 2005-11-16
thanks for your help.
I think I'd know how to follow/apply aysiu's advice if I could get passed "the black screen with white letters on it".I don't have the words to explain this right but I can't open anything with gedit.
Would it be correct to say I can't get to the graphical interface?and therefore I don't know how to modify/save changes in a text editor as explained in your posts.
please don't forget this is ABA (AbsoluteBeginnerAbsolutely).
good day

---

### Post by wadesmart on 2005-11-16
Ok. Im not sure what you just said for sure so let me respond to what I think you are saying.

If you go to Applications> Accessories> Terminal in Breezy, that will bring up the command line interface - the black thing with white letters. 

When that comes up you will have something that says x@x:~$
That is where you type in your command. 
One command that you can type in is: sudo gedit /etc/apt/sources.list  and then hit enter. Then a password: command will come up and you enter in your password. Wait a few seconds and a text app will open. This is the file that is being discussed about editing. 

You can do this also through System> Administration> Synaptic Package Manager. I personally think its harder that way but if you choose to do it you can get help on doing that. 

Does that help? 

Wade

---

### Post by xyz on 2005-11-16
[QUOTE=wadesmart]Ok. Im not sure what you just said for sure so let me respond to what I think you are saying.

If you go to Applications> Accessories> Terminal in Breezy, that will bring up the command line interface - the black thing with white letters. 

When that comes up you will have something that says x@x:~$
That is where you type in your command. 
One command that you can type in is: sudo gedit /etc/apt/sources.list  and then hit enter. Then a password: command will come up and you enter in your password. Wait a few seconds and a text app will open. This is the file that is being discussed about editing. 

You can do this also through System> Administration> Synaptic Package Manager. I personally think its harder that way but if you choose to do it you can get help on doing that. 

Does that help? 

Wade[/QUOTE]

thanks Wade and sorry for my lack of clarity!
I don't have access to"Applications> Accessories> Terminal in Breezy"!If I could,I think I'd know how to replace the sources.list which would appear in the text editor.(delete the text found there,replace it C/C and save).
About 'the black thing with white letters' is this:
I start the computer.I'm asked to choose Ubuntu or Windows.I start Ubuntu and the a 'black thing (screen) with white letters' comes up showing lots of [ ok ].And then instead of the nice brownish Ubuntu screen where one logs in/passwd, I read:

*I cannot start the X server(your graphical interface).It's likely that it's not set up correctly.Would you like to view the X server output to diagnose the problem? so I click YES - then: I will disable this X server for now.Restart GDM when it's configured correctly so I click OK*

and I'm back to 'the black background screen with white letters on it!"At this point and to be able to go on,I log in/passwd.I'm told (by another knowledgable person) gedit doesn't work here and I have to use nano or vim as text editors,which I did to somehow open the sources.list.
please tell me what I need to relate to you so as to be understood.thank you.

---

### Post by wadesmart on 2005-11-16
11162005 0820 GMT-5

Im still a totally newbie myself but, what I would do if I didnt have anything that I couldnt live without, I would just reinstall and see if that worked. That might not be the right choice for you, understanding more about your now described problem, but in my case, if something didnt work right off, I just reinstall. 

Wade

---

