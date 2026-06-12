---
title: "hmm first impressions of linux."
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Ludford on 2007-05-21
I just did I full install of linux and I have to say it looks quite nice. simple layout pleasing to the eye.

now it is time for my mega noob questions that you can all laugh at.

1) how do I change the time.

2) I imported an mp3 into music player but nothing seemed to happen.

3) when can I download the full install of beryl, I went over to there site but it seems to be a list of alot of programs.

EDIT: Cool I found out the wobble thing and the rotater is a part of it anyway without beryl.

---

### Post by smoker on 2007-05-21
hi, to change the time, go to system, administration, and select 'time and date'

you will need codecs to play mp3, probably the easiest way is to install 'automatix' from here:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Happy_Man on 2007-05-21
1. Right-click on the time, choose Adjust Date and Time, enter your password, and choose your timezone. Simple.

2. You need to install some plugins.... open up Add/Remove, search Gstreamer, and install every codec pack you see (should be four).

---

### Post by Kobalt on 2007-05-21
Ii'd suggest you to follow [these steps]("http://ubuntuforums.org/showthread.php?t=413624") to enable multimedia. And additionaly, I'd advise to stay away from Automatix.

---

### Post by Hobo Joe on 2007-05-21
> **Kobalt said:**
> Ii'd suggest you to follow [these steps]("http://ubuntuforums.org/showthread.php?t=413624") to enable multimedia. And additionaly, I'd advise to stay away from Automatix.

What's wrong with Automatix?

I find it very useful, and I know that it helped me make the jump from Windows to Ubuntu....

---

### Post by smoker on 2007-05-21
> I'd advise to stay away from Automatix.

Why? i have installed automatix dozens of times and never had a problem! i would recommend it to anyone.

---

### Post by aktiwers on 2007-05-21
I love Automatix too..  And Welcome by the way, I just read your other post.
Doesnt Feisty install the codecs automaticly when you click on a MP3 file?

---

### Post by TwistesdTexan on 2007-05-21
Automatix has change alot since I started using it. You now have the option of removing any software you install with it. Also it is a better GUI than B-4. I like it also.

---

### Post by Ludford on 2007-05-21
Yo talking over FF on my linux PC now.... Thanks for all the info, I basicly tried to open an mp3 and I let linux do its thing to get me updated.

I LOVE how that the add remove programs is like a list of all the free programs on the net

---

### Post by Hobo Joe on 2007-05-21
While were on the subject, I don't seem to have 'add/remove' programs in my menu.... Any ideas?

All I have is Synaptic.

---

### Post by aktiwers on 2007-05-21
I have no Idea Hobo Joe..
But I would advice Ludford to take a look at Synaptic as well, as it (correct me if im wrong) contains a lot more programs. 
Its in: 
System => Administration=>Synaptic

---

### Post by Ludford on 2007-05-21
cool,

On the subject of beryl, I looked at the guide for INTEL cards and all it says is type


sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.beryl-script

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup.beryl-script

echo "deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main" | sudo tee -a /etc/apt/sources.list

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get -y install beryl beryl-manager emerald-themes

sudo cp /usr/share/applications/beryl-manager.desktop /etc/xdg/autostart/beryl-manager.desktop

sudo cp /usr/share/applications/beryl-manager.desktop ~/Desktop/beryl-manager.desktop

echo -e "Logout now and then press \e[0;31mCTRL+ALT+BACKSPACE\e[0m to restart xorg" echo "Installation completed !"







Am I to understand that I simply enter this into the terminal and I then have th program downloaded and installed?

It tells me to enter my password after I press ENTER, but it dosn't seem to repond to keyboard imput then.

---

### Post by aktiwers on 2007-05-21
Yes that is currect.
You can copy paste the commands by Middle-Click on your mouse or with CTRL+C and SHIFT+INSERT to paste into terminal.

The pasword thing is normal, just type your Password and hit enter. Its just so people looking over your shoulder wont see what you are typing..  I guess.

---

### Post by Ludford on 2007-05-21
cool, One thing is I seem to have lost my cool rotating cube thing

Desktop effects is still on, but the 4 tabs at the buttom have disapeard to be replaced with one.

---

### Post by aktiwers on 2007-05-21
I think thats a bug or something..  I did this to fix it on my Machine:
Copy/paste into Terminal.
```

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
```

But this doesnt happend on Beryl, right?

---

### Post by Ludford on 2007-05-21
they have come back now when I relogged but my desktop seems to have diapeared... 

anyway, I entered the beryl code into the terminal but nothing definitive came up, like an installation wizard of a message confirming installation. am I doing it wrong?

I'm also getting problems with windows just displaying white in them.

---

### Post by EAL on 2007-05-21
> **aktiwers said:**
> I love Automatix too..  And Welcome by the way, I just read your other post.
Doesnt Feisty install the codecs automaticly when you click on a MP3 file?

I just installed ubuntu for the first time, and yes, when I tried to play an MP3 file I got a message saying I needed a driver, followed the prompts, and bingo - I was listening to MP3s.

---

### Post by aktiwers on 2007-05-21
EAL Great, then I remember correct :) And Welcome to Ubuntu!

> **Ludford said:**
> they have come back now when I relogged but my desktop seems to have diapeared... 

anyway, I entered the beryl code into the terminal but nothing definitive came up, like an installation wizard of a message confirming installation. am I doing it wrong?

I'm also getting problems with windows just displaying white in them.

Can you explain what exactly happends?
Did you copy paste the commands one at a time into the Terminal, and then hit CTRL+ALT+BACKSPACE? And log back in?

Try dissableing your Desktop effects and then go to:
Start menu=> System Tools

Isnt there a Beryl Icon there you can click?

---

### Post by Ludford on 2007-05-21
ah I didn't copy the line one by one, i'll try that now
't 
EDIT: its asking me the password after the second line of code, is this normal, its also saying " *whatever i type* isnt a directory"

EDIT 2: wait its done now, I think, I have the beyrl icon on my desktop

---

### Post by aktiwers on 2007-05-21
Does it say that on the first line?
Did you remember that there is a "space" betwen the directories?
like
sudo cp /etc/X11/xorg.conf     THERE IS A SPACE HERE /etc/X11/xorg.conf.backup.beryl-script

And so on?

---

### Post by Ludford on 2007-05-21
I have it now I can access the emerald program, Now I just need to find out the buttons for it.

---

### Post by aktiwers on 2007-05-21
Let us know what you need to know.
Beryl should be in:
Start menu=> System Tools=>Beryl
And emerald should be in
System => Preferrences=>Emerald Theme Manager

---

### Post by Ludford on 2007-05-21
got it all working perfectly, a semi transparent cube, and a really nice theme that fits in with my transparent futury look I wanted, and ofcourse the fire effect on closing.

Thanx for all the help

---

### Post by aktiwers on 2007-05-21
No problem! :)
When its time to change the look, remember to check out
[http://beryl-look.org/](http://beryl-look.org/)

Cheers!

---

