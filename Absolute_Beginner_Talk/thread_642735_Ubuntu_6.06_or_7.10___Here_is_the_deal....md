---
title: "Ubuntu 6.06 or 7.10 ?  Here is the deal..."
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Dragon43 on 2007-12-17
I have a running computer with 6.06 on it. (Installed off a CD) 
900 Hz processor
640 MEG of RAM
7200 RPM HD
100Hz Front Side Buss
IDE drives
Networked to my in house system, two 98se machines and one XP laptop.

( I need to keep Windows so... don't ask... LOL )

I finally really need to upgrade the (2) Windows boxes and they will be ..
XP - Pro
ASUS MB with AMD processors (2+GIG)
800+Hz Front Side Buss
2 GIG RAM
10,000RPM HD's (76 GIG) (sata)

I want/need it all networked. ( hard wire ) I use LinkSys.

I have my parts for the Linux box now ( same as above only 2 sticks of 512 for 1 GIG total) ( 150 GIG,  WD 10,000 RPM HD ) and I have put it together and installed 7.10 off CD from Ubuntu.

I'm not happy yet.  Took a while to get the places like 'youtube' to be able to play.  I have read all the threads and had help from Ubuntu people and I can't get the networking to fly. ( Still the old 98se machines which we are still using.)

Questions:::
Should I keep fighting 7.10?  Is it worth it?  I am not that savvy about this stuff. 
 I'm old, 64, and learning new is slow for me.  ;)

If you all do not convince me to stay with 7.1, how can I get all my "STUFF" from the 6.06 hard drive' (IDE) to my 7.1 on the sata HD?

Which Ubuntu will do the most without too much struggle on my part?

Anything else I should be paying attention to?

Opinions, advice and comments appreciated.

Thanks..

---

### Post by chadridesabike on 2007-12-17
one suggestion is to try using feisty instead of gutsy.  I had that networked with three windows machines quite nicely. 

moving the data there are two easy options:  burn to dvds or get an external drive, reformat it to either FAT32 or ext3 (ext3 is easier but windblows wont read it).

---

### Post by CCNA_student on 2007-12-17
I would suggest using Kubuntu 7.10. I found it to be very simple and easy to get to work. And if you want us to help you with your networking problem, could you please be more specific and tell everyone exactly what you did?

    Sin Cere,

    CCNA_student

---

### Post by jimrz on 2007-12-17
If I recall correctly, win98 does not have the built in networking abilities of the NT based versions, so you will need your ubuntu box, using samba, to serve as a winserver and handle the domain for them. Once you have moved to XP on yoour new win boxes this will no longer be needed. I have 2 laptops (1 dual boot with xp) + 2 desktops (1 dual boot with xp) running 7.10 + 1 file server running 7.04 and no problems networking any of them, no matter which side the dual boot boxes happen to be in, without having to establish/maintain a domain. As for 6.06 v 7.10, at the time I really liked 6.06 but find 7.10 to be far superior now ... your mileage may vary.

EDIT: btw, I am 61, so this stuff is not beyond those of our generation. ;)

---

### Post by Dragon43 on 2007-12-17
> **jimrz said:**
> If I recall correctly, win98 does not have the built in networking abilities of the NT based versions, so you will need your ubuntu box, using samba, to serve as a winserver and handle the domain for them. Once you have moved to XP on yoour new win boxes this will no longer be needed. I have 2 laptops (1 dual boot with xp) + 2 desktops (1 dual boot with xp) running 7.10 + 1 file server running 7.04 and no problems networking any of them, no matter which side the dual boot boxes happen to be in, without having to establish/maintain a domain. As for 6.06 v 7.10, at the time I really liked 6.06 but find 7.10 to be far superior now ... your mileage may vary.

EDIT: btw, I am 61, so this stuff is not beyond those of our generation. ;)

LOL, first, I completely agree with your sig ...

yeah, 98 is a pain.  I finally got to where the 98 machines can see the Linux but the password does not work.  the Linux box still says it can't display the networks.  It also has two domains now.  :: sigh ::  The one I use XXXX and one called 'mshome'.  Neither opens... :rolleyes:

I am not stressing over it ... YET...  And waiting until it is all XP is probably the best.... (going to be soon)  But ....  grrrrrr  Since I did gain a bit this afternoon  I'll keep trying.  I did the 

[sudo smbpassword -a & e thing and also the -L _a & e thing....
Have files as read & write but the network stuff is a little different from 6.06, seems to be less places to make settings changes...  Probably a good thing when it comes to me messing with stuff that ain't broke....

Thanks and bring me more....

---

### Post by Dragon43 on 2007-12-17
> **CCNA_student said:**
> I would suggest using Kubuntu 7.10. I found it to be very simple and easy to get to work. And if you want us to help you with your networking problem, could you please be more specific and tell everyone exactly what you did?

    Sin Cere,

    CCNA_student

What is the difference between Ubuntu 7.10 and Kubuntu 7.10?

Also, if I do an new install with the CD, will it pick up all the stuff I have downloaded with this install? I'm not sure what all I have done, I'm not sure I did all the 'terminal' stuff just like the threads and poster said.  It seems they always forget how I have no knowledge and leave the simple but necessary steps out.

For instance, I was supposed to type in the terminal the [sudo xxxx -L -a password ] and then do it again with an "e".. Could not do that without hitting 'enter' and it wanted a password before I could continue.  What password?  Wass up wit dat?

Stuff like that messes me up....

Thanks for helping and give me more please.

---

### Post by Sef on 2007-12-17
> What is the difference between Ubuntu 7.10 and Kubuntu 7.10?

They are different desktop environments.


As for updating, I would wait for Hardy Heron, 08.04 because it is the next stable version.  The desktop edition will be updated for 3 years and the server edition will be updated for 5 years.  Normally they are only updated for 18 months.

---

### Post by tgalati4 on 2007-12-17
Try Linux Mint.  It's based on Ubuntu, and a lot of the stuff that you want to configure is already done for you.  Linux Mint XFCE for older machines (Pentium III).

---

### Post by jrharvey on 2007-12-17
> **Sef said:**
> They are different desktop environments.


As for updating, I would wait for Hardy Heron, 4.08 because it is the next stable version.  The desktop edition will be updated for 3 years and the server edition will be updated for 5 years.  Normally they are only updated for 18 months.

haha, 4.08???? dont you mean 8.04??? Im just kidding.

---

### Post by Sef on 2007-12-17
> haha, 4.08???? dont you mean 8.04??? Im just kidding.

Congradulations! For spotting my mistake, you have won your choice of A) The Brooklyn Bridge B) The Sydney Opera House or C) The Great Wall of China.  :lolflag:

I did put that backwards.  Corrected now.

---

### Post by jrharvey on 2007-12-17
I will take the Sydney Opera House. That thing is cooooool :)    You know I was just joking right?

---

### Post by jimrz on 2007-12-17
> **Dragon43 said:**
> LOL, first, I completely agree with your sig ...

yeah, 98 is a pain.  I finally got to where the 98 machines can see the Linux but the password does not work.  the Linux box still says it can't display the networks.  It also has two domains now.  :: sigh ::  The one I use XXXX and one called 'mshome'.  Neither opens... :rolleyes:

I am not stressing over it ... YET...  And waiting until it is all XP is probably the best.... (going to be soon)  But ....  grrrrrr  Since I did gain a bit this afternoon  I'll keep trying.  I did the 

[sudo smbpassword -a & e thing and also the -L _a & e thing....
Have files as read & write but the network stuff is a little different from 6.06, seems to be less places to make settings changes...  Probably a good thing when it comes to me messing with stuff that ain't broke....

Thanks and bring me more....

'mshome' is the default workgroup name in samba. You can edit your conf file
```
sudo gedit /etc/samba/smb.conf
```
and change
```
workgroup = mshome
```
to
```
workgroup = <your XXXX>
```
also, while you are there, use the 'find' button at the top to locate "browseable" and at the first result change
```
;    browseable = no
```
to
```
     browseable = yes
```
notice that you need to delete the ";" at the begining of the line to uncomment the line. Then go down a few lines and do the same to  ' ;     writeable = no'. Save the file and close. This will eliminate the 'mshome' thing you are seeing, put all boxes in the same workgroup and may help with some of your other issues.

Thanks for the sig comment. There are still a few of us left.

---

### Post by Dragon43 on 2007-12-17
I did that  on the browseable thing
............................
> # Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
   browseable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

.............................  
And this was already like this
.............................................

> 
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = *XX*

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast 

Now I'm going to reboot and see what happens.....

---

### Post by Myglaren on 2007-12-18
Welcome to the forums **Dragon43**!

See, lots of excellent advice already.  Best place it the world for first class friendly help.

---

### Post by Dragon43 on 2007-12-18
Okay, the Linux machine shows icons for the other computer 
 but both icons link to the same Linux file I have shared.  Neither one goes to the Windows box.  I can click on the network symbol and it goes to the XX network symbol which when clicked goes to the same looking window as this and both icons link to the Linux box.

Now, this is what I see on the Windows box and it only gives me the "supply a password" box and no matter what I type in that I get the "Password is incorrect, try again" message.



So, what now????



Help.................

---

### Post by Dragon43 on 2007-12-18
:::: Sheesh ::::  just copy this and add the( h t t p : / / ) ::;without the spacing of course :::  to the front and put in your browser and it should give you the pictures.....IF you take out the space in the file type at the end....

shareimagesonline.com/files/yj0wjkcpgalffwourtin.png

that is the Ubuntu box and this is the windows box

shareimagesonline.com/files/tpkqgy2mdedyxvkq1gg5.jpg

How do we post picture here?  or links to pictures?

[IMG]http://shareimagesonline.com/files/yj0wjkcpgalffwourtin.png[/IMG]

Only one image at a time?

---

### Post by Presto123 on 2007-12-18
Either one of the desktop environments (IE: Gnome and KDE) depend on what you like, but I will say this:

Even though I came from a Window's environment, I really found Gnome to be more friendly for me. 7.04 is also a definite recommendation, as I use it on this computer, and 7.10 on my laptop. I honestly LIKE 7.04 better, but with my laptop, the 7.10 version had the correct drivers for my wireless.

So, in my opinion, I would suggest Gnome and 7.04. 

[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

---

### Post by Dragon43 on 2007-12-18
I added RAM to be at 2 GIG and I seem to have regressed on the netowrking.  But My Linux box boots so fast it might have gotten up first even though I wait to boot it boot so the Windopws box is up first.  Why you ask?  For some reason if the Linux  box is up first the network will not work.  Has always been that way for me since my first tries with 6.06.  I have no clue, just the way it is.  So will now reboot the Linux box and see if there is improvement....

---

### Post by Dragon43 on 2007-12-19
Not so's you'd notice.....

Hummmmmmmmm   

More ideas and opinions please......

---

### Post by rzrgenesys187 on 2007-12-19
> **CCNA_student said:**
> I would suggest using Kubuntu 7.10. I found it to be very simple and easy to get to work. And if you want us to help you with your networking problem, could you please be more specific and tell everyone exactly what you did?

    Sin Cere,

    CCNA_student

Kubuntu went well for me as well, although I didn't have to fight with Gutsy too much.  Truth is Feisty is just as good as Gutsy in my mind.  The only reasons i use it is it recognizes 1440x900 resolution for my laptop off the bat and it boots faster.  Either way you can't go wrong with Ubuntu/Kubuntu

---

### Post by Dragon43 on 2007-12-19
Right now I can boot to an 'online' conditon (entering name and password) in 80 seconds.  That is so much faster than anything I have ever had that I am estatic.

From power bar to asking for login stuff is 60 seconds flat.  I type slow and have satellite latency.

Can I back up to a second hard drive { (SATA)  to an (IDE)}with a simple command?  Or will I need to use some app?  Help !!!!!  ( I use the hard drive instalation disks to do this on my Win machines. I keep the 2 HD unpluged physically, no lightining strike or hacker is going kill that ... I hope...)

---

### Post by Myglaren on 2007-12-19
Did you install the quickstart 3 program?  The first option there is full or partial backup.

I haven't used it as I rarely do backups *(quote~Linus Torvalds:  "Real Men Don't Do Backups" /q  LT)* 
I don't have that much to back up as all the music can be re-acquired and the pictures are all made into photo CDs regularly, much of the rest resides online anyway.

Have a poke around with that and see how much damage you can do.

---

### Post by Dragon43 on 2007-12-19
Will do.  Need to ge the second HD hooked up.

Oh, why does my 'spell check' not work on this board?  It does other places. (FireFox)

---

