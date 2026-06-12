---
title: "need help installinf files..."
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by eastcoaststar on 2005-08-04
i looked around on here, and couldnt find what i needed to help me.  im looking for a p2p to install.  i downlaoded limewire, but i dont know how to install it.  

how do i install programs?  any help would br appreciated.  i knwo this has been asked before, and im sorry, i just couldnt find it.

---

### Post by GavinX on 2005-08-04
I think this is what you need:

[http://www.ubuntuguide.org/#limewire](http://www.ubuntuguide.org/#limewire)

Cheers,
GavinX

---

### Post by eastcoaststar on 2005-08-04
thanks for the quick reply, and for the link.
thanks again

---

### Post by eastcoaststar on 2005-08-04
i get confused on step 4, 5 7 and 8.    4 and 7  and 5 and 8 are the same basically, but im not sure what to do during those steps...

---

### Post by GavinX on 2005-08-04
[QUOTE=eastcoaststar]i get confused on step 4, 5 7 and 8.    4 and 7  and 5 and 8 are the same basically, but im not sure what to do during those steps...[/QUOTE]
No. the steps are not the same, although they look so. You are dealing with different files.

The parts of the instructions which are in black should be done using a console or terminal window (applications -----> system tools -----> terminal). Copy and paste the instructions in the terminal and press enter.

When you run the commands and a file opens up, just copy and paste the parts that it said should be in the file.

---

### Post by eastcoaststar on 2005-08-04
that was step 3.   the part in the black box, i did copy and paste into the prompt.  but step 4 had a black botted line around it, and im not sure what that means.   then step 5, im not sure eather.      step 3 i did fine though.

---

### Post by GavinX on 2005-08-04
When you run the last command in step three, a file will open up on the desktop. You then do this for step 4 (copy and paste "cd /opt/LimeWire......." into the file which opens up, not the terminal):

Insert the following lines into the new file

cd /opt/LimeWire/
./runLime.sh

You do the same thing in step 7 also, because when you run the last command in step 6 a different file will open up.

After you copy and paste the line in the file, click save in the File Menu (that is what steps five and eight are instructing you to do. forget about the "sample" that they show you, that is only to give an idea of how the file should look when you are finished.)

If you still have problems let me know.

---

### Post by eastcoaststar on 2005-08-04
i had to do step 3 a few tiems before another prompt (where i save it) poped up.   then in step 6,  i copy and paste what im supposed to, and it still isnt poping up for me to save it...

---

### Post by eastcoaststar on 2005-08-04
i just did it starting from step 1, and it worked perfectly fine.  thanks much for the help!

---

### Post by eastcoaststar on 2005-08-04
well...  i thought i got it right... its in my applications and all, but its not loading when i try to open it...

also... where can i download and how do i install the plugins for ubuntu?   i cant play mp3s, avis, mpgs, or anything...

i was installing realplayer, and it says... Copy nphelix.so to your Mozilla plugins directory and nphelix.xpt to your Mozilla components directory.
where is the plugins and components directory?

---

### Post by eastcoaststar on 2005-08-07
please someone?   i think i need to install java,  but every time i do, i get an error.  can anyone help me?   i need help...

---

### Post by TravisNewman on 2005-08-07
first off, outline the problems you're still having so we know what we're working with.

for java, see ubuntuguide.org specifically the "extra repositories." You'll need to have those enabled. Then, search for j2re in synaptic and install it. If you get errors from that, report back :)

As far as the realplayer issue, how did you install realplayer?

---

### Post by eastcoaststar on 2005-08-07
i tink whats giving me the most problems now is, when i enter a code in the terminal, it asks me for a password,  and i try to type my password, and it doesnt let me...

i will post the rest of my problems soon.

---

### Post by eastcoaststar on 2005-08-07
well first, i didnt know i had to change the extra repositories, so that helped alot,  thanks!
but  then i try to install J2SE Runtime Environment (JRE) with Plug-in for Mozilla Firefox...  and this is what i get...

sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  libgtk1.2
The following NEW packages will be installed:
  sun-j2re1.5
0 upgraded, 1 newly installed, 0 to remove and 61 not upgraded.
Need to get 30.5MB of archives.
After unpacking 89.1MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  sun-j2re1.5
Install these packages without verification [y/N]? Y
E: Some packages could not be authenticated

why wont it work?

---

### Post by TravisNewman on 2005-08-07
It doesn't matter if they aren't authenticated. That's very odd that it's kicking you back like that, when you're answering yes.

---

### Post by eastcoaststar on 2005-08-07
is it something i could be doing wrong?  idk what though

---

### Post by eastcoaststar on 2005-08-08
pleaseeee

---

### Post by GavinX on 2005-08-09
[QUOTE=eastcoaststar]is it something i could be doing wrong?  idk what though[/QUOTE]
Ok, tell you what follow these steps and I believe that all will be well afterwards:
In a terminal run the following command:
1. sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
2. sudo gedit /etc/apt/sources.list
3. When the sources file opens, delete everything that is in it and copy and paste the following into the file:

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

4. Save the file and close it
5. In a teminal do "apt-get update" (without the "")
6. Try to install j2re and limewire again, skipping the part which says to enable the extra repositories since they are now enabled.

Please report when you're done.

Cheers,
GavinX

---

### Post by eastcoaststar on 2005-08-09
well  when i go to do step five... this is what i get...


apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory


should i just re-install linux? hah

---

### Post by eastcoaststar on 2005-08-09
well well well... it all finally worked :-)
finalllly,   thank you for that walkthrough,  you helped me alot!

---

### Post by GavinX on 2005-08-09
[QUOTE=eastcoaststar]well well well... it all finally worked :-)
finalllly,   thank you for that walkthrough,  you helped me alot![/QUOTE]

I just got in from the road and I'm pleased to see that things worked out for you. Enjoy the aroma of Ubuntu.

---

### Post by eastcoaststar on 2005-08-09
thanks :-)
now that i have everything sorted out, i am very happy with ubuntu.

one last thing, what is a good program to burn CDs?  i was going to use gnomebaker, but i couldnt find the download

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=eastcoaststar]thanks :-)
now that i have everything sorted out, i am very happy with ubuntu.

one last thing, what is a good program to burn CDs?  i was going to use gnomebaker, but i couldnt find the download[/QUOTE]

My favorite is K3B:

[https://wiki.ubuntu.com/K3BHowto?highlight=%28k3b%29](https://wiki.ubuntu.com/K3BHowto?highlight=%28k3b%29)

---

### Post by GavinX on 2005-08-10
[QUOTE=poofyhairguy]My favorite is K3B:

[https://wiki.ubuntu.com/K3BHowto?highlight=%28k3b%29]("https://wiki.ubuntu.com/K3BHowto?highlight=%28k3b%29")[/QUOTE]
Yah, K3B is really good.

---

### Post by eastcoaststar on 2005-08-10
well  K#B it is,  thanks guys!

installed no problem, and works fine :-)  thanks much!

you all here (expecially gavinX)  helped my linux expreience ALOT  and made it great

---

### Post by poofyhairguy on 2005-08-10
[QUOTE=eastcoaststar]well  K#B it is,  thanks guys!

installed no problem, and works fine :-)  thanks much!

you all here (expecially gavinX)  helped my linux expreience ALOT  and made it great[/QUOTE]

Any time. Enjoy life and Ubuntu.

---

