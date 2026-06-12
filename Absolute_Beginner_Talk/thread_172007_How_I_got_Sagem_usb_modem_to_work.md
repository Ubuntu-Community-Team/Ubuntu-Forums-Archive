---
title: "How I got Sagem usb modem to work"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by phatdad on 2006-05-07
ADDED 18 MAY 06
Although this does work, there have been problems, ie 'modem not operational' errors, which meant I had to redo this and found a better way. Not many folk are viewing this post, but if anyone is having trouble, post a reply and I'll write up the esier way.

Original post;

This is a rundown of how I got my Sagem Fast 800 E3 modem going in Ubuntu. I am a newbie and don't pretend for one minute I sussed this out myself, but I had to go through loads of postings on forums to find a solution, so this 'guide' pulls it all together in the hope it saves someone else some time. Don't be fooled for a minute into thinking I have a full understanding of whats going on here, this is my first Linux week, so some explanations maybe a bit ropey... apologies but there you go. 

Please note, I am a newbie and cannot be held responsible for any damage to your computer or sanity this method may cause. My computer seems fine, my sanity...?

I had to compile (or whatever you call it) a driver for the modem. This all went pear shaped because, as far as I can explain this, my gcc version installed was different to the version used to compile the Breezy kernel. (Why is this?) So I had to change the installed gcc to 3.4 first, then sort the driver out. Some searching,  sweating, and near relationship breakdown later....... we have this.......

Check the kernel situation first. I looked gcc entries up in Synaptic and found I had version 4.0. I don't know how you check Breezy version, but from reading posts on forums I was sure it was version 3.4. If your situation is the same as mine then off we go. 
 
Get online somehow and download these four lots of files- 
 
cpp-3.4_3.4.4-6ubuntu8_i386.deb 
from [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb)
gcc-3.4_3.4.4-6ubuntu8_i386.deb
from [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb)
gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
from [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb)
Fast8x0_3-0-6.tgz
from [http://www.sagem.com/support/site/driver/Fast8x0_3-0-6.tgz](http://www.sagem.com/support/site/driver/Fast8x0_3-0-6.tgz)

Save these four downloads to a CD, and then stick the CD in your freshly booted up and logged on Ubuntu box. There are probably other ways to get the files onto your Ubuntu machine, eg USB memory stick, but I used a CD.

There are probably better ways of doing this next bit, but here's what I did. Open File Browser (Applications>Accessories>File Browser) and navigate to the folder with your name. (I'm Pd, so replace Pd from now on with your name. In File Browser Home>Pd)
You should see a folder in the window called Desktop. Right click next to it and create folder named "gcc-3.4" 

Copy the .deb files on the cd into this new folder. Leave the Fast8x0_3-0-6.tgz file alone for now. (With the File Browser open and showing your new gcc-3.4 folder, click on the CD icon on your desk top and drag the three .deb files onto the gcc-3.4 folder)

Close the CD window for now. (Am I allowed to call them windows?)

OK, now we're gonna start messing so check later replies to this post in case anything is wrong.

Log on as root-
(Applications>Accessories>Terminal then type sudo -s -H then enter your password at the prompt. This should change the command line prompt (or whatever it's called) to root@ubuntu/usr/sbin# or similar.)

Navigate to the gcc-3.4 folder by typing 
cd //home/pd/gcc-3.4
changing pd to your name of course

Then type in
sudo apt-get install build-essential
then
dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

(the | is by holding AltGr then top left key next to 1. Took me about 5 mins to suss that)

It should put something like this up

cpp-3.4 gcc-3.4 gcc-3.4-base
wrote 3 entries to output packages file

Your gcc-3.4 folder should have a Packages file in it now. The next step involves getting synaptic to load from local rather than the internet repositories (because there's no connection yet, but stick around!) You'll need to edit the sources list. Type
sudo gedit /etc/apt/sources.list

In the document that appears, look for all the lines starting "deb-src http" or "deb http" and add a # to the start of the line if there isn't one. Note, as they are now commented out they are ignored, but you'll need to reverse this. I added # THIS ONE to remind me later. 

Then  at the end of the document, add the line
deb file:///home/pd/gcc-3.4 ./
Replacing pd again with your name. Click save and go back to your terminal. Nearly there now.

Next install the gcc-3.4. Type
sudo apt-get update
then
sudo apt-get install gcc-3.4

Loads goes on, and it asks you to confirm a couple of things, which I agreed to as I thought what the heck. It was all OK it seems. Then you have to change to gcc-3.4. Type
export CC=gcc-3.4

Go back and alter those lines you commented out in the sources list by removing the # etc, and delete that last line you added. Same procedure as before to call up the sources list.

Now the driver bit. Click on the Cd icon on the desktop then the Fast8x0_3-0-6.tgz file and drag it onto your desktop. (You can delete this at the end of all this.) Click on the  Fast8x0_3-0-6.tgz file, and the File Roller shows you eagle-usb. With the File Browser showing desktop and your gcc-3.4 folder, drag eagle-usb across so it sits there with the others. Next you need that terminal where you are logged on as root to point at this new folder. Type
cd //home/pd/eagle-usb
The next stages result in a lot of output, and this post is epic already. So I'll just outline the stages. Type 
./appli_patch
then move down a level by typing
cd //home/pd/eagle-usb/eagle-usb-src
then type
./configure

Now here I messed up. As I had had several goes at different methods, I had to clean out the mess I'd made. i didn't suss this at first, but it seems if you have yes next to the eaglectrl, eaglestat, startadsl, or stopadsl entries at the end of all that that flies out, you have to do the following. Skip if they are all no.
Type 
make uninstall
then
make clean

Next make the driver. Type
make
then when it all calms down again, type
make install

Almost there. Type
eagleconfig

You'll have to enter the correct location code, mine was UK01.

This should all end in a message that says modem OK and configuration complete or something. 

To connect, you type
startadsl
to disconnect type
stopadsl

I haven't yet worked out how to start the modem any quicker than opening a terminal and logging on as root, using sudo -s -H,  before I can use startadsl. I leave this terminal open to then stopadsl when I want to disconnect. There is a way through using a launcher which I can't get working.

I hope all this helps. Any errors I will change if someone in the know could check over it for me. 
All this came from posts on the Ubuntu forum. Credit to all, but must name 
blastus
Malac
alastair

Off to bed I go. Good luck to all.

---

