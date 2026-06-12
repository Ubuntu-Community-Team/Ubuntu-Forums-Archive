---
title: "Follow the Newbie - New users problems and solutions"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by IainWood on 2006-04-29
This is more an information post.

I have just installed Ububtu on a duff old pc that was struggling to run windows XP, basically it was a machine no one used, so i thought to myself why not have a go a linux (odd sideline down knoppix then debian route then to Ubuntu)

First Hurdle was the good ol Nvidia drivers, man did I have fun with this.
As i found several solutions that didnt work (mainly cause i was being dumb) i thought id clear it up fopr anyone having the same problem

There is a Key order to doing this right.

Ok dont go running off editing the /etc/X11/xorg.conf file just yet!!!
I'm going to use a # to indicate what to type into the terminal so don't type the first # of any line!
First pop open a terminal and use

# uname -r 

that gives you the Kernel name, look at the last bit of it (in my case 686 but could be K7 ect)

this is useful if you are a total NOOB like me

then kickstart 
system-->administartion-->synaptic package manager

use the search facility and type in nvidia

you will get a list of things you need
NOW IMPORTANT
You will need!
1)kernel
2)driver
3)nvidia settings

if you have an older card you will need the LEGACY drivers (geforce 2 for me so i did), I found this out by trial and error but i'm sure a google search will turn up the right one for your card

remember that bit earlier (686 etc)! look for the linux kernel with nvidia (nvidia-legacy for older cards) and that bit at the end (as you are probably working in 640x480 this will take a bit of scrolling)

mark this for installation 

look on through for the nvidia-glx (or nvidia-glx-legacy for older cards)
tick that

nvidia settings is the only one (usually near the bottom) tick that

apply and wait ....................

ok now shutdown the computer *completely* dont fiddle with anything else just yet!!

once restarted you can log back in - graphics still naff? dont worry

go to terminal and type in

# sudo dpkg-reconfigure xserver-xorg

this starts up the setup facility

when it detects your graphics card it will probably deafult to 'nv' look in the list for 'nvidia' 

keep going through when it asks you if you want to use the framebuffer select NO
(why? - because whatever I did the system would not let me have the resolution 1280x1024 as it seemed to always try to set up in 24 bit mode - go figure)

keep going .....

when it asks what resolution you want your monitor to provide (assuming it autodetects) leave it be. you can remove all options here and it will go for the best possible!

finally the bit depth page. 
If you choose 24 bit! your card may not be able to get the resolutions it is capable of, so i'd go for 16 bit, unless you are incredibly perfectionist you wont notice a difference!
 
after the wizard completes shutdown again and restart

after you log in you should see the nvidia logo flash up before ubuntu starts!

to get rid of it do a google search - i kinda like it reminds me of the effort it took to get the damn thing working!

this is how i got my Nvidia GeForce2 on a Dell flatpanel Monitor to run at 1280x1024 16bit depth on ubuntu) (whew!!)

remember folks this was  a complete newbie to linux here so this was an achievement and a half after 10 hours trawling the web and trying things out editing files and everything which seemed to mess up other stuff (such as apt-get install kubuntu-desktop)

I now have this all working (mind you I did a fresh re-install to check it) 
The next entry will probably be about Kubuntu-desktop which is currently installing!

see you later

Iain Wood
noobie 
[http://www.woodit.co.uk](http://www.woodit.co.uk)

---

