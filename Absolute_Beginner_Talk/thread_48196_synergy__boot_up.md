---
title: "synergy / boot up"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by tospig on 2005-07-11
Hey guys, my friend told me to install Linux on my 2nd machine, so I did, and here I am. 

I have a windows machine, and a linux one, with one keyboard and one mouse, connected to windows machine.

I use synergy to allow the K & M to be used between machines much like a kvm switch. my question is this:

it's all fine and good once i've started linux, but before I boot it up, i have to unplug K & M from windows, and plug into Linux, to enable me to enter user & pass. What i would like is to have Synergy load on boot up, so that I don't have to plug in K&M when it boots up to enter my user/pass.

does anyone know how I go about doing this, or a way of doing this?

If so, a complete noob step by step guide would be greately appreciated (assume all i know how to do is open a terminal)

Thanks for any help :D


/end first post, woohoo

---

### Post by OuchIAteMyself on 2005-07-11
How the heck did you get synergy installed? The package installs, but won't run on mine. Did you use a package or did you build from source? I will be working on this issue as soon as I can get it installed.

---

### Post by tospig on 2005-07-12
is there anybody out there...

...that can help?

maybe not specific to my problem, but about how to make something run at boot-up before you have to log in??

---

### Post by darksbane on 2005-08-20
I want to do much the same thing, I've been looking around on the Synergy website and I came across this: [http://synergy2.sourceforge.net/autostart.html](http://synergy2.sourceforge.net/autostart.html)

> Synergy requires an X server. That means a server must be running and synergy must be authorized to connect to that server. It's best to have the display manager start synergy. You'll need the necessary (probably root) permission to modify the display manager configuration files. If you don't have that permission you can start synergy after logging in via the .xsession file.

Typically, you need to edit three script files. The first file will start synergy before a user logs in, the second will kill that copy of synergy, and the third will start it again after the user logs in.

The contents of the scripts varies greatly between systems so there's no one definite place where you should insert your edits. However, these scripts often exit before reaching the bottom so put the edits near the top of the script.

The location and names of these files depend on the operating system and display manager you're using. A good guess for the location is /etc/X11. Typical file names are:

   	   	xdm 	   	gdm
1 		xdm/Xsetup 		gdm/Init/Default (*)
2 		xdm/Xstartup 		gdm/PostLogin/Default (*)
3 		xdm/Xsession 		gdm/Sessions/Default (*, **)

*) The Default file is used if no other suitable file is found. gdm will try displayname (e.g. :0) and hostname (e.g. somehost), in that order, before and instead of Default.
**) gdm may use gdm/Xsession, xdm/Xsession or dm/Xsession if gdm/Sessions/Default doesn't exist.

For a synergy client, add the following to the first file: /usr/bin/killall synergyc sleep 1 /usr/bin/synergyc [<options>] synergy-server-hostname Of course, the path to synergyc depends on where you installed it so adjust as necessary.

Add to the second file: /usr/bin/killall synergyc sleep 1

And to the third file: /usr/bin/killall synergyc sleep 1 /usr/bin/synergyc [<options>] synergy-server-hostname Note that <options> must not include -f or --no-daemon or the script will never exit and you won't be able to log in.

The changes are the same for the synergy server except replace synergyc with synergys and use the appropriate synergys command line options. Note that the first script is run as root so synergys will look for the configuration file in root's home directory then in /etc. Make sure it exists in one of those places or use the --config config-pathname option to specify its location.

Note that some display managers (xdm and kdm, but not gdm) grab the keyboard and do not release it until the user logs in for security reasons. This prevents a synergy server from sharing the mouse and keyboard until the user logs in. It doesn't prevent a synergy client from synthesizing mouse and keyboard input, though.

If you're configuring synergy to start only after you log in then edit your .xsession file. Add just what you would add to the third file above. 

Anyways after reading through that and looking through my Ubuntu directories I found that the files that seem to require editing aren't found in the directories they give, but I did find them all, for the first one you have to go to:

/etc/gdm/init/

for the second file you have to go to:

/etc/gdm/postlogin/

and for the third one I'm not 100% sure but I think its either

/etc/gdm/postsession/

or

/etc/gdm/presession/

Someone will have to help me out on that.

Anyways, you have to edit the file in those directories to include the code from the Synergy site. However this is where I'm stuck. I can't edit the files because they require a root login to edit them and I don't know how to login as root since it didnt ask me to specify a password for root or anything when I installed Ubuntu, so any help in this would be greatly appreciated :)

---

### Post by tospig on 2005-09-05
i found out that to edit you'll want to use the command 

sudo gedit <filename>

(you dont' have to use gedit, any editor will do)

---

### Post by Insti on 2006-04-30
I wanted to make the synergy server run from my ubuntu (5.10) box. (update: still works in 8.04)
Here is what you need to do:

Make a directory in /etc to store the configuration:

```
sudo mkdir /etc/synergy
```

Setup my synergy server configuration file:
```
sudo gedit /etc/synergy/synergy.conf
```

To make the server run when gdm runs, but before anyone has logged in:

edit /etc/gdm/Init/Default:
```
sudo gedit /etc/gdm/Init/Default
```

Added the following lines in the middle of the file **BEFORE** the "sysmodmap=/etc/X11/Xmodmap" line:

```

SYNERGYS=`gdmwhich synergys`
if [ x$SYNERGYS != x ] ; then
        $SYNERGYS --config /etc/synergy/synergy.conf
fi

```

The only problem with that is once you log in it kills off the server, so you need to make it start again for you.
 
edited /etc/gdm/Init/Default:
```
sudo gedit /etc/gdm/PreSession/Default
```

Added the following lines in the middle of the file **BEFORE** the "XSETROOT=`gdmwhich xsetroot`" line:
```

SYNERGYS=`gdmwhich synergys`
if [ x$SYNERGYS != x ] ; then
        $SYNERGYS --config /etc/synergy/synergy.conf
fi

```

Log out and back in again.

The synergy server should now startup and run whenever your gdm session does.

---

### Post by airtonix on 2006-05-05
Ummm, im confused....because the server is what you run on your machine to send the keyboard and mouse singals to the remote machine........which leaves me wondering why you would want the server loading up on a machine that already has a keyboard and mouse on it....so im wondering .....your guide is for ....what? 

But i'll make a guess and say that your talking about setting up the client to run on the remote machine with the gdm server, so that you can login from the synergy server that serves the  keyboard and mouse data streams, rather than lean over....ruin your spine....and type in  your details...  

Am i right so far? sorry to be obtuse, but this needs clarification....for i run the server on my laptop....thus controlling the client running on my desktop......id o this at home and i do it at work.....for provids me with a psuedo twin head setup, that I find provides much better peformance that a twin head on a single computer...

---

### Post by Insti on 2006-05-05
[QUOTE=airtonix]Ummm, im confused....because the server is what you run on your machine to send the keyboard and mouse singals to the remote machine[/quote]

Correct.

[quote=airtonix]
which leaves me wondering why you would want the server loading up on a machine that already has a keyboard and mouse on it[/quote]

Because i want to send the keyboard and mouse signals to a client on another machine.
Your guess confused me, because you seemed to suggest something, and then give a completely different description of what you do. Which seems to be much the same as what I do. Unless the confusion happens because you think that the client computer must be the one with the keyboard and mouse attatched to it?

Here is what I do:

Computer A - Runs Linux - Has Keyboard and Mouse.
Computer B - Runs Windows - Has no keyboard or mouse.

Computer A runs synergy server on gdm startup + user login.
Computer B runs synergy client automatically on startup, and connects to the already running server on Computer A.

Now I can now log into and use my Windows machine using the keyboard and mouse attatched to my Linux machine.
(Computer A is used and 'on' a lot more than computer B)

Does that help?

---

### Post by nwgray on 2006-05-23
> **Insti]I wanted to make the synergy server run from my ubuntu (5.10) box. 
Here is what you need to do:

Make a directory in /etc to store the configuration:

```
sudo mkdir /etc/synergy
```

Setup my synergy server configuration file:
```
sudo gedit /etc/synergy/synergy.conf
```

To make the server run when gdm runs, but before anyone has logged in:

edit /etc/gdm/Init/Default:
```
sudo gedit /etc/gdm/Init/Default
```

Added the following lines in the middle of the file **BEFORE** the "sysmodmap=/etc/X11/Xmodmap" line:

```

SYNERGYS=`gdmwhich synergys`
if [ x$SYNERGYS != x ]  said:**
>  ; then
        $SYNERGYS --config /etc/synergy/synergy.conf
fi

```

Log out and back in again.

The synergy server should now startup and run whenever your gdm session does.
Admitted serious Linux noob here. What syntax would I use if I wanted to start the client and not the server (synergyc)? I run an XP and Ubuntu box side by side and it is working great. I just need synergyc to start automatically.

Thx

---

### Post by Insti on 2006-05-23
[QUOTE=nwgray]Admitted serious Linux noob here. What syntax would I use if I wanted to start the client and not the server (synergyc)? I run an XP and Ubuntu box side by side and it is working great. I just need synergyc to start automatically.
[/QUOTE]

These instructions should work for running the synergy client on your UBUNTU machine to connect to a locally networked computer running the synergy server. (I've not actually tried them myself.)
Let us know how you get on.

**NOTE:**
The <address of server machine> will probably be an ip address that looks something like 192.168.0.1 (DON'T put in the exact string <address of server machine>)

To make the client run when gdm runs, but before anyone has logged in:

edit /etc/gdm/Init/Default:
```
sudo gedit /etc/gdm/Init/Default
```

Added the following lines in the middle of the file **BEFORE** the "sysmodmap=/etc/X11/Xmodmap" line:

```

SYNERGYC=`gdmwhich synergyc`
if [ x$SYNERGYC != x ] ; then
        $SYNERGYC <address of server machine>
fi

```

The only problem with that is once you log in it kills off the client, so you need to make it start again for you.
 
edited /etc/gdm/Init/Default:
```
sudo gedit /etc/gdm/PreSession/Default
```

Added the following lines in the middle of the file **BEFORE** the "XSETROOT=`gdmwhich xsetroot`" line:
```

SYNERGYC=`gdmwhich synergyc`
if [ x$SYNERGYC != x ] ; then
        $SYNERGYC <address of server machine>
fi

```

Log out and back in again.

The synergy client should now startup and run whenever your gdm session does.

**NOTE:**
The <address of server machine> will probably be an ip address that looks something like 192.168.0.1 (DON'T put in the exact string <address of server machine>)

---

### Post by daesae on 2006-06-24
Thank you Insti, et al.

This method was by far the simplest and easiest way I have seen, and it was the first among many that worked.  I am now happily moving back and forth between GDM and KDE using my Windows machine's peripherials.

I am aware that Synergy can only run under an X server, but is anyone aware of a method that would allow me to use the keyboard without the X server?  Such an option would be convenient when updating video drivers and reinstalling my linux distro as I so often do(another psychiatric session on it own).

-James

---

### Post by MasterZ on 2006-07-03
Hello, 

I'm trying to start synergy on the login screen on a fresh install of Dapper. 
I followed this guide (and some others too but basically everyone says the same thing). 

I added the lines described in this guide, but synergyc won't start-up during the login screen... 

Normally, the synergy client put its logs in syslog, but I don't see anything there (no "client started" or something). 

How could I make sure that the files in gdm/Init and gdm/PreSession are really read during starup ?
Does anyone know where I could find troubleshooting informations to see what's going wrong ? 

Thanks, 

MasterZ

---

### Post by kBanshee on 2006-07-04
I have the same problem. Synergy starts fine when I login, but before login, it's not running..

---

### Post by MasterZ on 2006-07-04
I'm still searching for some solution to this problem, and I found something strange. 

I added the line :
```

touch /tmp/somefile 

```
in the /etc/X11/gdm/Init/Default file and started gdm again. 

I was surprised not to find any "somefile" existing in /tmp ... 

I'm beginning to wonder if gdm really reads that file at startup or not ... Does someone know about another file that could be used by gdm at startup ? 

I found some hints in the gdm documentation : 
```

When the X server has been successfully started, GDM will try to run the script called  Init/<displayname>. I.e.  Init/:0 for the first local display. If this file is not found, GDM will attempt to to run Init/Default.
```
But my directory on ly contains "Default" and "Default_Backup" ... 

Please help. 


Thanks,

MasterZ

---

### Post by Insti on 2006-07-04
[QUOTE=MasterZ]
I added the line :
```

touch /tmp/somefile 

```
in the /etc/X11/gdm/Init/Default file and started gdm again. 

I was surprised not to find any "somefile" existing in /tmp ... 

I'm beginning to wonder if gdm really reads that file at startup or not ... Does someone know about another file that could be used by gdm at startup ? 
[/QUOTE]

Great investigative work!

I've not moved to dapper yet, but try checking that the Default file has execute permission set. It should look something like:

```

ls -l  /etc/X11/gdm/Init/Default

-rwxr-xr-x  1 root root 2722 2006-04-30 10:17 /etc/X11/gdm/Init/Default

```

you also might need to specify the path to the touch binary:

```

/bin/touch /tmp/somefile

```

Another thing to try:

Log in to your Ubuntu box via ssh from another machine and check to see if there is a synergy process running:

```

ps -ef | grep synergy

root      8292     1  0 Jul03 ?        00:01:25 /usr/bin/X11/synergys --config /etc/synergy/synergy.conf

```

Sometimes it might take a while for the synergy processes to start talking to each other.

Let us know how you get on..

Insti.

---

### Post by MasterZ on 2006-07-05
Hahaaa :D 

You found it ! 

The file "/etc/X11/gdm/Init/Default" did not have execute permissions. 

I wonder if it is a bug or not, because "/etc/X11/gdm/PreSession/Default" has execute permissions. (It is a fresh install so I did not modify anything yet, except running automatrix). 

Anyway for the persons who still have the same problem, just do 
```
sudo chmod +x /etc/X11/gdm/Init/Default
```
and it should be ok. 

Thanks again Insti ! :o 


MasterZ.

---

### Post by nwgray on 2006-07-24
Insti
   Looking thru my subscribed threads, I realized I never let you know how your steps worked for me. One word - flawlessly. My synergy client now logs in before anyone and I don't have to use a manual KVM anymore. 

Thanks so much!

---

### Post by mage2 on 2006-08-21
I am using KDE and need to know what files to use to make synergyc startup. 
thanks

---

### Post by richbl on 2007-01-18
> **Insti said:**
> 

The synergy server should now startup and run whenever your gdm session does.


Just a quick note to let you know that this runs flawlessly under Edgy (6.10). 

Nice howto.

Thanks.

---

### Post by inveigle on 2007-05-04
this works for feisty
great solution

---

### Post by zorog on 2007-06-07
Thanks Insti  exelent instuctions now i can finaly do away with the keyboard i used to have to use just for loggin in.

synergy rocks, its a shame development seams to have stalled!

Have fun,
Simon.

---

### Post by Chuq on 2007-06-12
The instructions on the Synergy site (linked earlier) worked for me, with the exceptions of:
*The third file being /etc/X11/gdm/PreSession/Default as suggested above
and
*I only added "/usr/bin/synergyc <ip-address>", not all three lines (ie. not the killall and sleep commands)

---

### Post by dionnow on 2007-07-03
Well I've been through all the steps stated above, and then some, and still encountering a problem.  When i SSH in with a differnt PC before I use the login prompt on my ubuntu box I do see the synergy client running, as well as seeing it connected on my server, yet I'm unable to utilize the mouse and keyboard.  I see that proccess is getting killed off and then reopening.. and it does work after log in.... Any ideas?

---

### Post by Insti on 2007-07-03
I don't have an answer, but I have some questions that might lead to one:

Which user is the synergy client running as?
Does it have permissions to the X Server it's trying to use?
Does it start up after the X Server?
Does it know which display to use?
If you use the "As Server" setup described, does THAT work for you?

Good Luck.

---

### Post by dellinger on 2007-09-07
Hello all,

Just wanted to post a follow-up for any Kubuntu users (i.e., using KDM) that may not know where the right files are.

If you want the synergy client to start up pre-login, follow Darksbane's original instructions from page one (where he quotes the instructions from sourceforge). On Fiesty and KDE3, modify the following files instead of the posted ones:

1 xdm/Xsetup gdm/Init/Default                     ->       /etc/kde3/kdm/Xsetup
2 xdm/Xstartup gdm/PostLogin/Default        ->       /etc/kde3/kdm/Xtartup
3 xdm/Xsession gdm/Sessions/Default          ->       /etc/kde3/kdm/Xsession

Also note that in his quote, multiple commands ended up in the same line. I.e., in Xsetup, I added the following 3 lines:
/usr/bin/killall synergyc
sleep 1
/usr/bin/synergyc <hostname>

That worked perfectly for me, so I hope it helps!

---

### Post by BrendanM on 2007-09-08
Has this been resolved already? I was able to get synergy working automatically before + after login on my machine. If people still need help, I can post what I did.

---

### Post by BrendanM on 2007-10-05
Since somebody requested it, I was able to get Synergy working before and after login by adding certain lines to some of GDM's files, as follows:
To /etc/gdm/Init/Default
At the start of the file, add
```

/usr/bin/killall synergyc
sleep 1
/usr/bin/synergyc --restart -n <name_of_local_machine> <name_of_server>

```

To /etc/gdm/PostLogin/Default add
```

/usr/bin/killall synergyc
sleep 1
/usr/bin/synergyc --restart -n <name_of_local_machine> <name_of_server>

```

To /etc/gdm/PreSession/Default/  add the synergy related lines as below

```

 IFS=$OLD_IFS 
  echo "$OUTPUT"
}

# synergyc process, running as root, ends here. This is the last script in #the gdm login sequence before things start running as user. Added by Brendan
/usr/bin/killall synergyc
sleep 1

# Set background color
XSETROOT=`gdmwhich xsetroot`
if [ "x$XSETROOT" != "x" ] ; then
```

I've included a little context on the last one to show you where to put the synergy stuff, since I don't think it goes at the very start. If you don't have all of these files, you may need to create them by copying the example file and making it an active file. I remember having to do that for at least one file.

These are links where I got my information:
 [https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)
[http://fro.instantspot.com/blog/index.cfm/ubuntu](http://fro.instantspot.com/blog/index.cfm/ubuntu)
[http://synergy2.sourceforge.net/autostart.html](http://synergy2.sourceforge.net/autostart.html)

This works for me, your milleage may vary.

---

### Post by jeremyp123 on 2007-10-05
I don't know if this is just 7.10 specific, but from what I've seen it should work for other releases...

Using the above instructions I could get logged on, but the Synergy didn't start when I hit the desktop.

I'm sure there's a harder way to do this but for this n00b's sanity:

1: Follow the instructions above AFTER you have installed Synergy
-1.a For beginners that may not know - open a Terminal window and add "sudo gedit" (minus quotes) to the beginning of the files listed above... like this "**sudo gedit /etc/gdm/Init/Default**"
-1.b What that basically says is: *"give me Super User access to use gedit to edit the file Default in the /etc/gdm/Init/ folder"*
-1.c Once you have edited all three files with the code above then move to step 2.

2. On your main menu click System > Preferences > Sessions

3. On the Startup Programs tab click Add
-3.a Set the name to "Synergy Startup" (again minus the quotes)
-3.b Set the command to "**/usr/bin/synergyc --restart -n <client address> <server address>**" (minus the quotes and replace server and client address with the proper IP addresses/Names)
-3.c Set the comment to anything you like... It's not essential...

Restart and try it out... It won't hurt anything if you leave a keyboard and mouse attached to the client... If it works then you can detach them and you're ready to go...

P.S. Big thanks go out to the posters that helped me get this thing working! :)

---

### Post by BrendanM on 2007-10-08
That's good Jeremyp123. I wonder if we should formalize this into a HOWTO thread?

---

### Post by xlr8ed on 2007-10-30
> **Insti said:**
> These instructions should work for running the synergy client on your UBUNTU machine to connect to a locally networked computer running the synergy server. (I've not actually tried them myself.)
Let us know how you get on.

**NOTE:**
The <address of server machine> will probably be an ip address that looks something like 192.168.0.1 (DON'T put in the exact string <address of server machine>)

To make the client run when gdm runs, but before anyone has logged in:

edit /etc/gdm/Init/Default:
```
sudo gedit /etc/gdm/Init/Default
```

Added the following lines in the middle of the file **BEFORE** the "sysmodmap=/etc/X11/Xmodmap" line:

```

SYNERGYC=`gdmwhich synergyc`
if [ x$SYNERGYC != x ] ; then
        $SYNERGYC <address of server machine>
fi

```

The only problem with that is once you log in it kills off the client, so you need to make it start again for you.
 
edited /etc/gdm/Init/Default:
```
sudo gedit /etc/gdm/PreSession/Default
```

Added the following lines in the middle of the file **BEFORE** the "XSETROOT=`gdmwhich xsetroot`" line:
```

SYNERGYC=`gdmwhich synergyc`
if [ x$SYNERGYC != x ] ; then
        $SYNERGYC <address of server machine>
fi

```

Log out and back in again.

The synergy client should now startup and run whenever your gdm session does.

**NOTE:**
The <address of server machine> will probably be an ip address that looks something like 192.168.0.1 (DON'T put in the exact string <address of server machine>)


Best set and only working instructions I have seen on this issue, thanks greatly!

---

### Post by shakajumbo on 2007-11-09
:KS :KS :KS :KS :KS 

5 Gold stars!!!

Thanks works GREAT in Gutsy Gibbon too :)

---

### Post by GodsDead on 2008-01-27
Oh thank you so much for that mod =]
thats helped me out Soo much!
:guitar:

---

### Post by PertinaxVir on 2008-03-20
Excellent and easy solution!  Thanks bunches!  This saved me hours of tinkering.

---

