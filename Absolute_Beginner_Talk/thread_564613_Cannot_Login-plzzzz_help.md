---
title: "Cannot Login-plzzzz help"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by greenleaf on 2007-10-01
I enabled the "automatic login" option... but forgot to choose a user name (i had 3 users option)... now when the computer restarted... i'm not getting anything...just a blank screen..the computer doesn't know which user to automatically logon, coz i didn't choose any user(how stupid of me)....neither do i get login screen... i'm locked out of my home:(  ...  

can anybody tell me how to disable 'automatic login' without logging in...i can start ubuntu in recovery mode... but dont know which command to enter to disable "automatic login'

---

### Post by ukripper on 2007-10-01
in  terminal mode type follwoing:

```
sudo vim /etc/gdm/gdm.conf 
```

and find line with** AutomaticLoginEnable**  and change it to **false**

and then 
```
startx
```

---

### Post by greenleaf on 2007-10-01
thanks for your reply....
i'm a newbeee
here is what i did

ran ubuntu in recovery mode....
logged in as root
typed 'startx'
i got my desktop (i'm still logged in as root)
i tried to change 'login window' from system>administrator.... but it displayed that GDM is not running... i tried your above command too and it gave the file.. a part of it i'm displying here

[daemon]
# Automatic login, if true the first local screen will automatically logged in
# as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=


as you can see' AutomaticLoginEnable' was already false
i then restarted.... and then the same problem..blank screen..i just cannot log on...plz i need further help.. thanks again for your time and reply...i'll be waiting

---

### Post by phidia on 2007-10-01
Is this a new install and did you ever have a gui desktop with this install?
I'm thinking that something could be wrong with X too..what kind of blank screen are you getting e.g black, beige..something else? Are there any error messages, and what version of ubuntu are you using? 

Added:

What happens if you login with your username and then try to "startx"? Root logins to x are disabled in ubuntu but if you are logged in as a regular user you should be able to start x provided there's nothing else wrong.

Ok I re-read your 1st post here-it seems like it could be the auto login problem. If you are unfamiliar with vim I wouldn't recommend  it. (You need to learn the keystrokes for vim to know how to save and edit)
You could use a live cd like ubuntu to mount the partition your install is on and then use something like gedit to read and check the files.

---

### Post by greenleaf on 2007-10-01
i have recently installed 7.04 feisty fawn.....it worked beautifully for a week...thought i could flush out windows forever....until i messed up with automatic login by turning it on.... i get a black screen with rotating (waiting) cursor.. i remember to have checked someother box too in login window options but am not sure what it was....could that be the trouble?

---

### Post by phidia on 2007-10-01
Automatic login should just work-and I understand the reasons someone might want that i.e no other users or just ease of use. It should actually be designed so that you can't select (or in this case forget to select) an option that will then foul up the desktop launch.

Have you tried to login with your username, from commandline, and then do "startx"?
Please try that and then report what happens-if you get your gui desktop back again you can either unselect auto login or make sure a user IS selected.

---

### Post by greenleaf on 2007-10-01
ok i tried and i could login as user(i.e. gl) and tried to run startx and this is what i got

```
root@GreenLeaf-desktop:~# login gl
Password: 
Last login: Mon Oct  1 23:54:54 2007 on pts/2
Linux GreenLeaf-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
gl@GreenLeaf-desktop:~$ startx
xauth:  creating new authority file /home/gl/.serverauth.4973
X: user not authorized to run the X server, aborting.
xinit:  Server error.
Couldnt get a file descriptor referring to the console
gl@GreenLeaf-desktop:~$
```


why can i not change the login settings when i'm logged in as root like right  now... sys>administration>login window...... gives the msg that 
"GDM (The GNOME Display Manager) is not running. 
You might infact be using a different display manager such as KDM or xdm. if you still want to use this feature start GDM yourself or ask your system administer to start GDM"

in ref. to my second post.... i think my automatic login is disabled...or is it not?

---

### Post by phidia on 2007-10-01
> **greenleaf said:**
> ok i tried and i could login as user(i.e. gl) and tried to run startx and this is what i got

```
root@GreenLeaf-desktop:~# login gl
Password: 
Last login: Mon Oct  1 23:54:54 2007 on pts/2
Linux GreenLeaf-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
gl@GreenLeaf-desktop:~$ startx
xauth:  creating new authority file /home/gl/.serverauth.4973
X: user not authorized to run the X server, aborting.
xinit:  Server error.
Couldnt get a file descriptor referring to the console
gl@GreenLeaf-desktop:~$
```


why can i not change the login settings when i'm logged in as root like right  now... sys>administration>login window...... gives the msg that 
"GDM (The GNOME Display Manager) is not running. 
You might infact be using a different display manager such as KDM or xdm. if you still want to use this feature start GDM yourself or ask your system administer to start GDM"

in ref. to my second post.... i think my automatic login is disabled...or is it not?


It's sometimes difficult to precisely diagnose a problem at a distance so we're still going through the troubleshooting as it were. 
The fact that you get a black screen with the hourglass cursor is telling us something is trying to start but either isn't configured right or is segfaulting? 
I'm not at home-on my ubuntu install currently..but how are you getting to the commandline?
Are you doing Alt+Ctrl+F1? or does the CLI eventually come up on it's own?
Anyway after you login at the commandline, as a regular user, can you "sudo startx"? (be sure to login as the 1st user created on this install)
Try that and hopefully that will start x. Good luck. I'll be here for a bit more and will check later when I'm home.

---

### Post by greenleaf on 2007-10-01
First of all, thank you for your interest and time..it is greatly appreciated by new comers like me..

i can run ubuntu in recovery mode. there it asks me for my root password..i enter it.. and then run "startx" ..note that i can login as "gl" ( i.e. my administrator username) in the recovery mode itself..and then run "startx"...but it gives the same comment.. so i run "startx" under root..and my desktop shows up...i can then open the terminal and run commmands...thats how i get to the commandline..

but i'm not able to change login settings..it tells me that "GDM (The GNOME Display Manager) is not running.
You might infact be using a different display manager such as KDM or xdm. if you still want to use this feature start GDM yourself or ask your system administer to start GDM"

if i donot run ubuntu in recovery mode, it starts in normal mode automatically and thats when i get that pitch black screen with spinning cursor...

your help is greatly appreciated..thank you

---

### Post by phidia on 2007-10-01
> if i donot run ubuntu in recovery mode, it starts in normal mode automatically and thats when i get that pitch black screen with spinning cursor...

I suggest waiting a few minutes with that cursor indicating activity. (you may get an error message that will reveal more)
But assuming it either fails to commandline or even stays that way;  Press these keys at the same time > Alt+Ctrl+F1 You should get a commandline from doing that. Login at that screen with your regular user name NOT root, and try to do startx from there. Hope that works.

---

### Post by gamerteck on 2007-10-01
Nothing to see here :P

---

### Post by coolen on 2007-10-01
> **greenleaf said:**
> i can run ubuntu in recovery mode. there it asks me for my root password..i enter it.. and then run "startx" ..note that i can login as "gl" ( i.e. my administrator username) in the recovery mode itself..and then run "startx"...but it gives the same comment.. so i run "startx" under root..and my desktop shows up...i can then open the terminal and run commmands...thats how i get to the commandline..

So, were you trying to run startx from the terminal on your desktop? That'd definitely be a problem.

Just a thought, if what you're doing doesn't work: go to the command line (Ctrl + Alt + F1) and type in
```
sudo /etc/init.d/gdm restart
```
If you have auto-login disabled in the configuration file...this may work.
If nothing else, it might give us some more useful output.

---

### Post by natewhipple on 2007-10-02
I too am experiencing the same problem.  however I did not enable the auto login.  I did however check a box but do not remember the exact wording of the text next to it.  I have followed the above steps with these results.

when watching the black screen with the spinning cursor after several minutes there was no error returned it just continued with the blank screen.

I tried the startx command and it returned a error no 3.  

other results were the same as green leaf

any help would be appreciated for I to am new to ubuntu.  I have run it for just over a month now and without a doubt prefer it over windows.

natewhipple

---

### Post by greenleaf on 2007-10-02
@ **phidia**

i tried to boot ubuntu in normal mode.. but sorry, the cursor doesn't seem to get tired of spinning (even after 1 hr)


@ **coolen**
i logged in to desktop under root in recovery mode and tried your command to start GDM... HURRAY!!! it worked.. apparenly GDM started and i could open the 'login window' and disable automatic login... Now when i restarted and booted in normal mode, the login window appears and i could login through my regular user account.. And just when i thought the problem was solved... i noticed a small glitch..... the 'switch user' function is not working!!. If i've to login as different user i've to 'Logout' but cannot 'switch user'... if i select 'switch user', the login window appears and on logging in as a dif. user... the screen goes blank..and this time it is completely white screen... 

for your information.. i've disabled the 'Enable Accessible Login" in 'login window' under 'accessibility'... is that is what is causing problem? or do 've to change someother setting in 'login window' (Recently i've tampered with 'login window' options) :confused:

@ **natewhipple**

try whatever command i had entered, it might work for you.. or give more details about your problem... these fellows surely can come up with something..

Anyways... Ubuntu Community Rocks!!!  :guitar:

---

### Post by natewhipple on 2007-10-02
okay, so I booted up the computer from the live cd to see what it is that I had done in the login window settings.  the box that I had unchecked was, Include all users from /etc/password (not) for NIS.  I also added two of the users to the include list.

the next time that I went to reboot I was getting the black screen with the spinning courser.

following the instructions given to greenleaf.  in recovery mode using command line I typed in the command:  sudo vim /etc/gdm/gdm.conf

I made sure that I also did not  make the mistake of checking the box for automatic login, it was set to false

I then still using command line typed in startx

Ubuntu came up in recovery mode however, when I attempted to open the window to change the login window settings I received the error window:



GDM( the Gnome Display Manager) is not running

You might in fact be using a differnet display manager such as KDM( KDE Display Manager) or XDM
if you still want to use this feature either start GDM yourself or ask your system administrator to start GDM



I then closed that error window and logged out to command recovery mode command line and used the command: sudo /etc/init.d/gdm restart

I once again received tha black screen with the spinning cursor 

any suggestions on what to do next would be appreciated.  UBUNTU is new to me

thanks

---

### Post by coolen on 2007-10-02
Any chance you could give us the contents of gdm.conf?

Edit: Sorry, it seems that /etc/gdm/gdm.conf stores the default settings for gdm. If all else fails, removing the settings from /etc/gdm/gdm.conf-custom (the settings, not headings and comments) and restarting gdm should get you back to the default setup.

---

