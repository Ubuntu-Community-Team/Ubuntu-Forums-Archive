---
title: "RDP From Windows To Ubuntu"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Brother_Marquis on 2006-06-16
Hey folks,
Anyone have any luck remoting an Ubuntu PC from a Windows XP PC?  I would like to have an RDP session open at my work machine (XP) into my home PC (Ubuntu)?

Thanks for any imput you may have!

---

### Post by loell on 2006-06-16
vnc is the way :)

---

### Post by Brother_Marquis on 2006-06-17
OK, I obviously did a n00b move somewhere along the line.  I upgraded to Drake and  followed this thread to get VNC server services working on my PC...
[http://www.ubuntuforums.org/showthread.php?t=191564&highlight=vnc](http://www.ubuntuforums.org/showthread.php?t=191564&highlight=vnc)

It removed everythinng (I mean, everything  :sad:) when I chose to install vnc4server from synaptic package manager.  I didn't catch the message before I chose to install it but it was something like 'multiple items will need to be removed to install this package'.  Sounded reasonable to me however it was obvious that this was the wrong move from the beginning.  I realized I should stop the removal process but I figured that stopping it in the middle would have negative consequences.  After it finished and I rebooted, I found that I removed  the desktop shell, all applicatoins (i.e. browsers, games, openoffice).......pretty much everything.  I could log on,and that was about it.

Anyway, I'm back to a fresh intall of Drake this morning and would still like to get access to this PC from my work PC (Windows XP).  If someone could tell me where I went wrong and what steps I need to take, that would be great.  I'm somewhat proficient with PCs but the more detail, the better I'll be.

---

### Post by loell on 2006-06-17
maybe that should work now,   there are a number of threads that when upgrading to dapper and then installing apps causes dapper to be not stable, i don't know if its just me. ;) .    when you install an app via synaptic, you can always click cancel while it is still downloading, and it won't affect your system, not unless it has finished downloading and started to install.

---

### Post by Brother_Marquis on 2006-06-18
So do I need VNC-common?  I no longer see a package for VNC4SERVER

---

### Post by loell on 2006-06-18
when i do a search in my cache, there is vnc4server :)

---

### Post by Brother_Marquis on 2006-06-19
That's weird.  I don't see it.  Anyway, I have some progress!!

I enabled the remote desktop features and set a password on my local PC through Ubuntu's System Preferences.  I downloaded and installed 'tightvnc' on another Windows PC on my home network.  I was able to connect to the Ubuntu PC!!  But I have more questions/comments:

 - The remote session's graphical interface from the Windows PC was plain awful.  I could barely make out the words in the menu system.  I'm used to the graphics for Windows XP RDP session, which are almost perfect.  Is this a result of TightVNC or a limitation of Ubuntu's remote desktop ability?  What is the prefered VNC client I should run on a Windows system?

 - When I involked the remote session from the Windows PC, I walked over to the Ubuntu PC and noticed that the screen was not locked.  In other words, when I was remotely accessing my Ubuntu PC, anyone in front of my Ubuntu PC would see what I'm doing.  Is there a configuration option that will allow me to lock the Ubuntu session once I remote in?  You know, just like Windows RDP feature?

I realize I'm a Windows person trying to get the same features in Ubuntu so don't flame me....;).  These are things I need to work in order for me to consider this as a viable replacement for Windows.

Thanks, loell, for your help so far.  I appreciate it.

---

### Post by loell on 2006-06-19
[QUOTE=Brother_Marquis]That's weird.  I don't see it.  Anyway, I have some progress!!

I enabled the remote desktop features and set a password on my local PC through Ubuntu's System Preferences.  I downloaded and installed 'tightvnc' on another Windows PC on my home network.  I was able to connect to the Ubuntu PC!!  But I have more questions/comments:

 - The remote session's graphical interface from the Windows PC was plain awful.  I could barely make out the words in the menu system.  I'm used to the graphics for Windows XP RDP session, which are almost perfect.  Is this a result of TightVNC or a limitation of Ubuntu's remote desktop ability?  What is the prefered VNC client I should run on a Windows system?

 - When I involked the remote session from the Windows PC, I walked over to the Ubuntu PC and noticed that the screen was not locked.  In other words, when I was remotely accessing my Ubuntu PC, anyone in front of my Ubuntu PC would see what I'm doing.  Is there a configuration option that will allow me to lock the Ubuntu session once I remote in?  You know, just like Windows RDP feature?

I realize I'm a Windows person trying to get the same features in Ubuntu so don't flame me....;).  These are things I need to work in order for me to consider this as a viable replacement for Windows.

Thanks, loell, for your help so far.  I appreciate it.[/QUOTE]


lol :D , I don't have the energy to flame you :)
plus i'm usually not into that, and i was a windows person myself a long time..
so i understand the frustrations and or feelings ;) 

anyhow, i think that's vino not the vncserver that you're using
since you can not see the vncserver on you synaptic

you need to edit sources.list by

     sudo gedit  /etc/apt/sources.list

uncomment the sources by removing # sign
and save it then do

sudo apt-get update

the applications list, etc will be downloaded, after it has finished downloading, depending on internet speed, then go back to synaptic

then search vnc, then i think vnc4server will show up, then install it.. :)

---

### Post by loell on 2006-06-19
after that for high resolution vnc
i don't know if this would depend on the resolution capacity of your graphics card
but to achieve high resolution you could execute vncserver by

vncserver -geometry 1600x1200 -depth 24

---

### Post by irv on 2006-06-19
I was having some problem with VNC myself, and started a thread back in April. See link below.

[http://www.ubuntuforums.org/showthread.php?t=164772]("http://www.ubuntuforums.org/showthread.php?t=164772")

Maybe this will help answer your questions? Take a look.

Remember you need to install a VNC viewer on your Window machine that can be downloaded from the Internet.

---

### Post by Brother_Marquis on 2006-06-19
Great, I'll try these when I get home.  What about the public session on my remote computer?  Will VNCSERVER make it private?  And as far as I can tell, there are many VNC clients for Windows.  Is any one better than another.

Thanks again, I appreciate your patience.

---

### Post by Brother_Marquis on 2006-06-19
[QUOTE=irv]I was having some problem with VNC myself, and started a thread back in April. See link below.

[http://www.ubuntuforums.org/showthread.php?t=164772]("http://www.ubuntuforums.org/showthread.php?t=164772")

Maybe this will help answer your questions? Take a look.

Remember you need to install a VNC viewer on your Window machine that can be downloaded from the Internet.[/QUOTE]

I'll try this too and report back.  thanks.

---

### Post by Brother_Marquis on 2006-06-19
Installed vnc4server and frustrated....no icon shows and no readily available documentation.  Kind of frustrating cuz I don't know the common things like where something is installed.

I'll start research how to start VNC4SERVER but if you guys know and can tell me faster, great!

---

### Post by loell on 2006-06-19
basically, when you like to search for a certain program,
you can click the terminal console

and type 

whereis application_name

as for vncserver its    >>>

          whereis vncserver


the output would be


          vncserver: /usr/bin/vncserver /usr/bin/X11/vncserver         
          /usr/share/man/man1/vncserver.1.gz

or you can just type in the terminal console

vncserver

to execute the program

---

### Post by Brother_Marquis on 2006-06-20
OK, I have successful remote sessions and have the video resolution thing worked out.  I spend about three hours trying to configure my PC to open a new session when I remote in so no one can see what I'm doing.  I followed the instructions in three different threads on the subject but didnt' have any success.  Any change I made resulted in the same.....remoting into my Ubuntu PC in a publicly viewed session.

---

### Post by Brother_Marquis on 2006-06-30
Folks,
Anyone have any idea how to help?  I just don't want to connect into a remote PC and have my session on the remote PC viewed by anyone near the remote machine.

Thanks.

---

### Post by raptros-v76 on 2006-06-30
with vnc4server? nobody near the vnc4server computer can see your session. vnc in a way combines ssh with xserver to provide a session that doesnt need a screen, just a remote veiwer

---

