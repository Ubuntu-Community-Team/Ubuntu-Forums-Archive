---
title: "Two dumb questions on networking..."
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by sheeep on 2006-11-09
Is a wireless adapter supposed to be displayed in the Network settings as "Wireless" or simply "ethernet connection"...

Right now I have the drivers for my adapter installed, the hardware recognized, but the only two things under the "connections" tab in Network Settings is "Ethernet connection" and "Modem connection".

And, will ubuntu pick up networks automatically or do you have to enter the IP or network name manually?

Thanks.

---

### Post by AndyCooll on 2006-11-09
Depends on your wireless adaptor, but typically they'll be displayed as ra0 or wlan0 or something similar. And yes it would be referred to as your wireless connection.

eth0 refers to your ethernet/wired connection.

:cool:

---

### Post by sheeep on 2006-11-09
So uhh, any suggestions on what should be done when its not picking up the adapter as wireless?

---

### Post by jordanmthomas on 2006-11-09
What kind of wireless card do you have?  It may be that you have to install the firmware for it.  For example, Fedora does not ship with firmware for my 2200G card so I have to install the firmware or it just sees the card as an ethernet connection (which, of course, doesn't work).

---

### Post by jordanmthomas on 2006-11-09
And, to answer your second question:  once you get it working, you should be able to select from a list in System --> Administration --> Networking when editing your wireless connection.

Also, you may want to check out network manager, it'll let you choose on the fly

---

### Post by Darrenlaid on 2006-11-09
My connection is wireless and it shows at the top panel eth1.

---

### Post by jordanmthomas on 2006-11-09
True, but it is identified as wireless and not as ethernet, right?  
(My wireless connection is eth1 as well)

---

### Post by sheeep on 2006-11-09
Its a microsoft MN-510, I've read alot about it and really don't understand.

I installed the drivers with ndiswrapper, the hardware is recognized, but nor as wireless. 

Also found this thread:

[http://www.ubuntuforums.org/archive/index.php/t-106700.html](http://www.ubuntuforums.org/archive/index.php/t-106700.html)

stating:

> I got the MN-510 to work on my parents' machine using linux-wlan-ng. The prism2_usb module loads automatically when you plug in the device, then you send a couple of commands to load the linux-wlan-ng drivers per the docs, then start the DHCP client.

The connection was a bit flaky at first until I followed someone's suggestion of sending the first linux-wlan-ng setup command twice in a row (I don't remember the whole string, you'll find it in the docs, but it's the one that includes prism2_usb DORESET=1). That seemed to prevent the connection from shutting down after a few hours.

I think I installed the correct linux-wlan-ng but I dont have any idea, and the prism2 didn't load automatically.

---

### Post by sheeep on 2006-11-09
I'm trying to install a different, newer linux-wlan-ng, and after un-tarring the file the instructions simply say run 'make config' which doesn't seem to be a command...

---

### Post by zaboura on 2006-11-09
Okay i know how you feel , and no its not two dumb questions on networking that you are asking ! actualy you ve just made it clear to me that there is alot of desperate people out there that need help in the IT field ...
anyhow the network or wireless cards appears as a normal card
it called CPU its in the mother board so the best thing to do in case its not working is to tip water or any flamable liquide on the mother oard so you cant see anything on the screen and if you are lucky to see anything you would be lucky of escaping out of a major fire accident ! anyways on microsoft policy when you tip the water you should apply the call of 000 or 911 it depends on the country you are at...
anyways for any aditional question please call me so i can provide you with my knowledge :evil:

---

### Post by zaboura on 2006-11-09
Okay i know how you feel , and no its not two dumb questions on networking that you are asking ! actualy you ve just made it clear to me that there is alot of desperate people out there that need help in the IT field ...
anyhow the network or wireless cards appears as a normal card
it called CPU its in the mother board so the best thing to do in case its not working is to tip water or any flamable liquide on the mother oard so you cant see anything on the screen and if you are lucky to see anything you would be lucky of escaping out of a major fire accident ! anyways on microsoft policy when you tip the water you should apply the call of 000 or 911 it depends on the country you are at...
anyways for any aditional question please call me so i can provide you with my knowledge

---

### Post by sheeep on 2006-11-09
... If you're gonna post something trying to be humorously ridiculous with a sense of sarcastic intelligence at least spell correctly?

---

### Post by chocbar31 on 2006-11-10
try

sudo ./configure

sudo make

sudo make install

or 

sudo ./configure && sudo make && sudo make install

---

### Post by jordanmthomas on 2006-11-10
...I wouldn't suggest configuring and making as root.
```
./configure
make
sudo make install
```
would be the correct way.

---

### Post by sheeep on 2006-11-10
Thank you guys so much, I'll give that a try.

---

### Post by sheeep on 2006-11-11
Still doesn't seem to work, now just says no such file or directory. What directory should I be putting in after un-tarring the file?

---

### Post by jordanmthomas on 2006-11-11
after you untar it, find the folder it extracted to in nautilus.
Open your terminal and type cd and press space
Then, drag the file from nautilus into your terminal.  Press enter and you should be in the right directory.

You can type
```
ls
```
to see what is in your current directory.  If there is no configure script, look for an appropriate directory to cd into.

---

### Post by sheeep on 2006-11-11
Is nautilus something different than just the file browser? I.E. am I looking for where the file got un-tarred to or am I just going to the home folder and finding it there.

I tried it with the command

cd /home/sheeep/linux-wlan-ng-0.2.5.tar.gz

and got returned

bash: cd: /home/sheeep/linux-wlan-ng-0.2.5.tar.gz: Not a directory

err, so I guess I need to find where it got un-tarred to? where or how would I go about doing that?

thanks again.

---

### Post by jordanmthomas on 2006-11-12
a) nautilus is indeed the file browser
b) Now that I know exactly where things are, I can give you some commands to run.

Open a Terminal
type
```
cd /home/sheeep
tar xvzf linux-wlan-ng-0.2.5.tar.gz #to untar into a new directory called linux-wlan-ng-0.2.5
cd linux-wlan-ng-0.2.5 # enter the new directory
ls # so you can see what's in there
./configure # should run the configure script
make # should compile it
sudo make install # should install it

```
If you run into any problems, just post back.

---

### Post by sheeep on 2006-11-12
Got up to the ls part, it listed the files... 

./configure returned

.bash: ./configure: No such file or directory

---

### Post by jordanmthomas on 2006-11-12
What does ls output when you run it.
Also, what does pwd output?
I get:
```
add-ons  config.in  COPYING  etc  LICENSE   man     scripts  THANKS
CHANGES  Configure  doc      FAQ  Makefile  README  src      TODO

```

AND NOW I SEE THE PROBLEM.
Configure has a captial C
use that instead of a lowercase

---

### Post by Papa-san on 2006-11-12
OK... from another nOOb to someone I think might be new as well...

When you do the commands shown above, don't include the pound sign (#) or the info aftre it on each line... The # is shorthand for "don't include the following, it is for you to understand" or when editing a file, it remarks out the line (Makes your computer ignore it)

---

### Post by sheeep on 2006-11-12
Oh my, you have no idea how happy this makes me.

Thank you, sooooooo much. It got to the y/n question part.

If this works in full for the adapter, I'm going to do a little tutorial writeup of what i went through and post it on all the threads I've made in relation to this so anyone else searching will hopefully be able to be helped.

---

### Post by jordanmthomas on 2006-11-12
> **Papa-san said:**
> OK... from another nOOb to someone I think might be new as well...

When you do the commands shown above, don't include the pound sign (#) or the info aftre it on each line... The # is shorthand for "don't include the following, it is for you to understand" or when editing a file, it remarks out the line (Makes your computer ignore it)

Just so you know, including the # doesn't hurt anything either because, like you said, bash ignores anything after it.  It never hurts to know what it means though!  :D

---

### Post by sheeep on 2006-11-12
Configuring worked, but it stopped me saying the linux source directory and the linux source tree is incomplete or missing. I guess the default wasn't the correctly detected one.

Any quick answer to this? I'm searching the sites the how to file gives right now

... Just guessing, its supposed to be some file in the /lib folder, so err... Which would that be?

---

### Post by jordanmthomas on 2006-11-12
It probably involves symbolically linking (basically a shortcut) your kernel sources to /usr/src/linux

This is sort of complicated, but try and bear with me.
```
cd /usr/src
ls

```
The kernel sources you have should be listed here.  These are want you want to link, so it would be something like this
```
sudo ln -s /usr/src/*your kernel directory* /usr/src/linux
```
This will make a link to *your kernel directory* named linux.
After that, most programs will compile better.

---

### Post by jordanmthomas on 2006-11-12
Someone else has probably had the same problem, though, and it might be better to find something that worked rather than listen to me...

---

### Post by sheeep on 2006-11-12
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Quick bit of googling brought that up, I guess I might as well try it. I've got enough coffee next to me to keep me going.

By the way, when I went into the /usr/src directory, and typed ls, nothing was returned.

---

