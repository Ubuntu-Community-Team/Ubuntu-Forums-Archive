---
title: "How to install Google Earth"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by mdknaebel on 2007-05-18
Im running Ubuntu 7.04 on a computer, and I want to put Google Earth on.  When I download the .bin file, I dont know what to do next

Any Help?
Thanks!

---

### Post by hyper_ch on 2007-05-18
Easiest way is to add the medibuntu repository to your sources. Google for medibuntu and there you'll find a howto.

---

### Post by 65536 on 2007-05-18
first make it executable
chmod +x /home/yourname/Desktop/file.bin
then run it
/home/yourname/Desktop/file.bin

EDIT: or just install automatix, it's in there

---

### Post by Nachoj on 2007-05-18
for automatix

first: sudo apt-get update
then find the appropriate version here [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by taurus on 2007-05-18
Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```
You have to install Automatix just to install Google Earth!

---

### Post by Killtown on 2007-05-18
I just downloaded Google Earth following directions in [this post]("http://ubuntuforums.org/showpost.php?p=2618301&postcount=2"):


```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```


Did that in the terminal box, it extracted (or whatever it did), but now what?  I don't see where it loaded.

---

### Post by taurus on 2007-05-18
> **Killtown said:**
> I just downloaded Google Earth following directions in [this post]("http://ubuntuforums.org/showpost.php?p=2618301&postcount=2"):


```
wget http://dl.google.com/earth/GE4/GoogleEarthLinux.bin
sh GoogleEarthLinux.bin
```


Did that in the terminal box, it extracted (or whatever it did), but now what?  I don't see where it loaded.

Look in Applications -> Internet.

---

### Post by Killtown on 2007-05-18
> **taurus said:**
> Look in Applications -> Internet.
It's not in there.  Is there a way to search for it?

---

### Post by taurus on 2007-05-18
```
find ~ -name googleearth -print
-or-
sudo find / -name googleearth -print
```
You don't remember where you installed it?

---

### Post by Killtown on 2007-05-18
> **taurus said:**
> ```
find ~ -name googleearth -print
-or-
sudo find / -name googleearth -print
```
You don't remember where you installed it?
Ok, I know what I didn't do,  after entering the 1st code in the terminal, it came to a new line of code that i didn't hit enter again.  silly me.

Thanks for you help.

---

### Post by linmix on 2007-06-08
I followed the same instructions but got an error message:
> $ sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.1.7076.4458..........................................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!


---

### Post by Faud on 2007-09-25
> **taurus said:**
> Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```
You have to install Automatix just to install Google Earth!


what does "chmod 755 GoogleEarthLinux.bin" exactly tell the terminal to do ?

---

### Post by mysticmatrix on 2007-09-25
> **linmix said:**
> I followed the same instructions but got an error message:

You have downloaded the wrong version(64 bit one)

---

### Post by mysticmatrix on 2007-09-25
> **Faud said:**
> what does "chmod 755 GoogleEarthLinux.bin" exactly tell the terminal to do ?

Tell to make your file executable.
Same as right clicking a file and changing its permissions.

---

### Post by misfitpierce on 2007-09-25
No... Download the binary like you have to home folder
Then type in terminal

sudo sh FILENAME.bin

Installs and done...

---

### Post by SpiritIsReality on 2007-09-25
howdy

thanks, all

trails

---

### Post by kteagan84 on 2007-09-25
This is what worked for me.

First, add the medibuntu repository:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

and
```

sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

and then

```
sudo apt-get update
```

this will set up the medibuntu repository

Then I did this:
```

sudo aptitude install googleearth
```

and press "yes" for all of the license agreement prompts that come up.

After that, you should be able to go into applications-->internet-->Google Earth

this worked for me without a problem, however, it does not have the latest version (Google Sky) so you may have to find another tutorial to get this.

---

### Post by Kilz on 2007-09-25
> **mysticmatrix said:**
> You have downloaded the wrong version(64 bit one)

There is no 64bit google earth, what are you saying is wrong?

---

### Post by Wolfie Lee on 2007-09-26
EDIT: or just install automatix, it's in there[/QUOTE]

Apparently, NOT ANYMORE...have been trying to get it to load ALL DAY, and it keeps saying unable to download...try later...
Just thought U's Guys should Know...

SO...I will just attemp the command line instructions here on the posts and hope for the best.

---

### Post by Wolfie Lee on 2007-09-27
Thanks for the lines of code, KTeagan!:grin:

They worked perfectly, BUT...my console did NOT accept a "Y" input or give any other way to accept licence agreement.....So, since there was a new repository, I just opened up Synaptic, and it took over from there...Thought others with a similar prob would like to know.  (Feisty / alternative, non-graphical install...)

---

### Post by R_U_Q_R_U on 2007-09-27
> **Wolfie Lee said:**
> Thanks for the lines of code, KTeagan!:grin:

They worked perfectly, BUT...my console did NOT accept a "Y" input or give any other way to accept licence agreement.....So, since there was a new repository, I just opened up Synaptic, and it took over from there...Thought others with a similar prob would like to know.  (Feisty / alternative, non-graphical install...)

Thanks! This worked great. I was sitting looking at the terminal <ok> and thought "great, I'll never get this thing installed." Then I opened synatptic and wamo I was cruising in Google Earth!

---

### Post by Wolfie Lee on 2007-09-29
> **R_U_Q_R_U said:**
> Thanks! This worked great. I was sitting looking at the terminal <ok> and thought "great, I'll never get this thing installed." Then I opened synatptic and wamo I was cruising in Google Earth!

No problem RUQRU, I'm just a NOOB, too, and still learning a lot...I figured it could help somebody....:cool:

---

### Post by telemetry on 2007-10-14
Thank you for those lines of code - worked really well for me.
Thank you.

---

### Post by jazzz337 on 2007-10-16
> **taurus said:**
> Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```
You have to install Automatix just to install Google Earth!

used the code looked like everything went well. Found it in applications no problem. How ever when I click it I get the splash the screen goes blank and then the log in screen for ubuntu comes up and that is all.

any ideas?
okay go it running upgraded to doit but got it thank you to every one for your help

---

### Post by alb@nian on 2007-10-18
> **jazzz337 said:**
> used the code looked like everything went well. Found it in applications no problem. How ever when I click it I get the splash the screen goes blank and then the log in screen for ubuntu comes up and that is all.

any ideas?
I'm using ubuntu 7.04 I installed it this way and it's working ok.

---

### Post by niceguy123 on 2007-10-19
1st 

I got stuck in stage 3. 

then I tried downloding googleearthlinux.bin from their site. Idownloaded it but couldn't run it.

then I found[ Medibuntu]("https://help.ubuntu.com/community/Medibuntu") help page. Which helped me run the medibuntu repository. and then I ran the last code here ```
sudo aptitude install googleearth
```

OK, now I've got googleearth in the internet bar.

BUT - when I try running it. Its opening page comes up and then my computer restarts.

Help anyone?

Thanks.

> **kteagan84 said:**
> This is what worked for me.

First, add the medibuntu repository:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

and
```

sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

and then

```
sudo apt-get update
```

this will set up the medibuntu repository

Then I did this:
```

sudo aptitude install googleearth
```

and press "yes" for all of the license agreement prompts that come up.

After that, you should be able to go into applications-->internet-->Google Earth

this worked for me without a problem, however, it does not have the latest version (Google Sky) so you may have to find another tutorial to get this.

---

