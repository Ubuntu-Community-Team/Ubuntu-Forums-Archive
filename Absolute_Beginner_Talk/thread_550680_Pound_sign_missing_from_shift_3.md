---
title: "Pound sign missing from shift 3"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by addisor on 2007-09-14
Really strange, the pound sign is missing from shift 3, HELP?


Got a wireless keyboard that did work once! Tried a serial keyboard and its the same.

---

### Post by justleen on 2007-09-14
are your locale settings OK?

other wise, you'll have to digg into xmodmap

getkeycodes - get and display the current mapping of scancodes to display codes (kernel function)
xmodmap - modify what happens for particular key(s) (X function)

---

### Post by addisor on 2007-09-14
got this but not to sure how to edit it

rob@rob-desktop:~$ sudo getkeycodes
Plain scancodes xx (hex) versus keycodes (dec)
for 1-83 (0x01-0x53) scancode equals keycode

 0x50:   80  81  82  83  84   0  86  87
 0x58:   88 117   0   0  95 183 184 185
 0x60:    0   0   0   0   0   0   0   0
 0x68:    0   0   0   0   0   0   0   0
 0x70:   93   0   0  89   0   0  85  91
 0x78:   90  92   0  94   0 124 121   0

Escaped scancodes e0 xx (hex)

e0 00:    0   0   0   0   0   0   0   0
e0 08:    0   0   0   0   0   0   0   0
e0 10:  165   0   0   0   0   0   0   0
e0 18:    0 163   0   0  96  97   0   0
e0 20:  113 140 164   0 166   0   0   0
e0 28:    0   0 255   0   0   0 114   0
e0 30:  115   0 150   0   0  98 255  99
e0 38:  100   0   0   0   0   0   0   0
e0 40:    0   0   0   0   0 119 119 102
e0 48:  103 104   0 105 112 106 118 107
e0 50:  108 109 110 111   0   0   0   0
e0 58:    0   0   0 125 126 127 116 142
e0 60:    0   0   0 143   0 217 156 173
e0 68:  128 159 158 157 155 226   0 112
e0 70:    0   0   0   0   0   0   0   0
e0 78:    0   0   0   0   0   0   0   0
rob@rob-desktop:~$ sudo xmodmap
xmodmap:  up to 2 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock      
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_R (0x71)
mod2        Num_Lock (0x4d)
mod3      
mod4      
mod5        Scroll_Lock (0x4e)

---

### Post by kombipom on 2007-09-14
What output are you getting when you press Shift-3 ? 

Have you checked in System->Preferences->Keyboard ?

---

### Post by addisor on 2007-09-16
3 is the output of shift 3. 

My keyboard is set as generic 104, despite it actually bing a microsoft wireless comfort keyboard 1.0A, why i select this keyboard i get an error message every boot up.

---

### Post by stig on 2007-09-29
> **addisor said:**
> 3 is the output of shift 3. 

My keyboard is set as generic 104, despite it actually bing a microsoft wireless comfort keyboard 1.0A, why i select this keyboard i get an error message every boot up.

I have exactly the same problem - shift 3 gives me 3, when it used to be the pound sign. Has a solution been found by addisor?

sudo getkeycodes gives exactly the same result as shown by addisor, and sudo xmodmap gives the same result except for the line:
lock        Caps_Lock (0x42)

The keyboard is set to "uk". My keyboard, like addisor's, is set as generic 104 because when I try to set the correct Logitech keyboard (or any of the other generic 105-key, 102-key etc) I get:
Error activating XKB configuration
The result of xprop -root | grep XKB
The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

The pound sign was lost after I got a new monitor and had to change screen resolution settings. The monitor should be on 1280 but the maximum I had in my settings was 1024. I followed one of the threads in this forum, advising to use the command sudo dpkg-reconfigure xserver-xorg

This took me through a very long series of settings, some of which meant little to me, but once started I had to guess some of them and carry on. It solved the monitor problem because I now have 1280 in my resolution settings - but I've lost the pound sign on shift 3!

I hope someone can help!

---

### Post by stig on 2007-09-30
Solved! I followed some of the advice on this page:
"Question #1719 in Ubuntu - Error activating XKB configuration"
[https://answers.launchpad.net/ubuntu/+question/1719](https://answers.launchpad.net/ubuntu/+question/1719)

See the post in that thread by csm888 which is as follows:

[INDENT]cd /etc/X11/gdm/PostLogin
sudo cp Default.sample Default

To file 'Default' add
xmodmap -e 'keycode 12 = 3 sterling'[/INDENT]

For those like me who don't know much about Linux or programming and don't normally use Terminal, this is what I did... (experts stop reading here!)

Open Terminal (i.e. Applications/Accessories/Terminal). Copy and paste the first line:
cd /etc/X11/gdm/PostLogin
into Terminal. Hit return. Copy and paste the second line:
sudo cp Default.sample Default
into Terminal and hit return. Enter password when requested.

This has made a new file called Default in the directory PostLogin (which is located at /etc/X11/gdm/).

Now type:
sudo Gedit
into Terminal to open the text editor in root mode (so that you have authority to modify the file). Go to File System, and navigate through the folders etc, X11, gdm to the PostLogin diretcory. Open the file called Default. Copy the line:
xmodmap -e 'keycode 12 = 3 sterling'
and paste it at the end of the Default file. Save the file.

Close applications and hit Control-Alt-Backspace to restart. You should now have recovered the £ sign.

---

### Post by addisor on 2007-10-10
Well done Stig, I'll be trying that shortly.

---

### Post by YoYoSan on 2007-10-20
Just discovered the same problem with a logitech wireless keyboard after upgrading to gutsy so thought it useful to bump this post - about to try the fix.

---

### Post by addisor on 2007-10-22
Worked a treat, thanks. Just about to upgrade to Gutsy, so at least i'll know the fix.

---

### Post by i-Buntu-2 on 2007-10-23
Hi,

I'm now on Ubuntu 7.10 (Gutsy) which I upgraded from a clean install of 7.04 (Feisty Fawn).

I was unable to find the Default.sample file in 

/etc/X11/gdm/PostLogin

as described above however I did find it in 

/etc/gdm/PostLogin

After editing the file as described I now have 3£3£3£ again!!

For anyone else who was unable to locate the file in the original location my alternative instructions would read:

cd /etc/gdm/PostLogin
sudo cp Default.sample Default

To file 'Default' add
xmodmap -e 'keycode 12 = 3 sterling'

Please refer to the post above by Stig (4 posts up) for the complete instructions

>>> Kudos to Stig for the original troubleshooting and resolving of this problem

---

### Post by Handssolow on 2007-10-25
I also noticed a few hours ago that my shift 3 gave a 3 too so I came looking for a solution here. Many thanks Stig and i-Buntu-2 I just followed your instructions and I've got my £ sign back.

Is it just a Gutsy issue?

---

### Post by fatdadkev on 2008-02-16
I am running 7.10 Gutsy GIbbon - and after an update (most likely me messing with Ubuntu) I lost the £ sign.

The command  xmodmap -e 'keycode 12 = 3 sterling' works but on a reboot you lose the £ sign again.

I tried the fix by putting the command into Default in the /etc/X11/gdm/PostLogin directory but by default this directory does not exist in 7.10 so I added the file etc - no joy.
I cleared the files out back to where it was and decided to adopt the simplest solution I could think of.

My fix was to go to SYSTEM > PREFERENCES > SESSIONS

Add a new start up command 

Give it a name (Mines called "Keyboard Pound sign")
Then paste the command ( xmodmap -e 'keycode 12 = 3 sterling') single quotes work so copy it and paste it in (Screenshot attached)

Save this and restart.

Not the most elegant of solutions but it works for me and no messing with files.

---

### Post by buttlodge on 2008-03-14
Thankyou, thankyou Fatdadkev
For a complete beginner with Ubuntu this is the one to use, it has also go rid of an error I had at start up which was "Error Activating XKB Configeration".
... hopefully one day I'll understand this stuff properly and dump Microsoft.:)[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by geezerone on 2008-04-03
I am having this problem in gutsy after it was working after fresh install but then had to reconfigure xorg.conf the usual way (dpkg...) to fix resolution too large problem. Now I have no pound sign as above. Have chosen 105 kbd layout. This xmod workaround worked but what is behind the problem???

Also getting error when trying to select 'non-generic' kbd too. :(

Get the following error:

```
 Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10300000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
```

---

### Post by DarkMadder on 2008-05-12
This fix works great in 8.04 except the folder is different. you can find the Default.sample file in:
[INDENT][FONT="Courier New"]/etc/gdm/PostLogin[/FONT][/INDENT]
i.e. there's no X11 folder in the path.

---

### Post by teaker1s on 2008-05-17
[http://ubuntuforums.org/showthread.php?p=4671032]("http://ubuntuforums.org/showthread.php?p=4671032")

---

### Post by NickD-NLUG on 2008-06-19
> **stig said:**
> Solved! I followed some of the advice on this page:
"Question #1719 in Ubuntu - Error activating XKB configuration"
[https://answers.launchpad.net/ubuntu/+question/1719](https://answers.launchpad.net/ubuntu/+question/1719)

See the post in that thread by csm888 which is as follows:

[INDENT]cd /etc/X11/gdm/PostLogin
sudo cp Default.sample Default

To file 'Default' add
xmodmap -e 'keycode 12 = 3 sterling'[/INDENT]

<snip by NickD-NLUG>

Close applications and hit Control-Alt-Backspace to restart. You should now have recovered the £ sign.

Nice, thank you for this.  It's been bugging me for ages and I finally decided to fix it... took all of thirty seconds ;)

By the way, as a temporary fix you can just paste "xmodmap -e 'keycode 12 = 3 sterling'" into a terminal window and it'll fix it for your current session without needing to Ctrl-Alt-Backspace.

---

