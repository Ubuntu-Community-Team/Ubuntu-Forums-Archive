---
title: "MPlayer help....."
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by windbreaker13579 on 2005-11-07
I am very new to ubuntu..... I just installed today.... I am trying to figure out how to install things. Could someone walk me through how to install mplayer. I have already  downloaded it from the mplayer site. Help would be very apprecated.

---

### Post by Kapre on 2005-11-07
[QUOTE=windbreaker13579]I am very new to ubuntu..... I just installed today.... I am trying to figure out how to install things. Could someone walk me through how to install mplayer. I have already  downloaded it from the mplayer site. Help would be very apprecated.[/QUOTE]

windbreaker13579 - Mplayer is in Synaptic. Click on System----->Administration=====>Synaptic Package Manager ------>look for Mplayer. 

After seeing Mplayer --- Install it.

K

---

### Post by Xian on 2005-11-07
Please do some searches in the wiki for these topics.
Also search the forum. This is a well covered subject.

[How-To Install Mplayer](https://wiki.ubuntu.com/MplayerInstallHowto?)
[Restricted Formats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by bored2k on 2005-11-07
[LIST=1]
[*]```
sudo gedit /etc/apt/sources.list
```
[*]Remove everything there and change it with these lines: [http://www.rafb.net/paste/results/dKHDRJ53.html](http://www.rafb.net/paste/results/dKHDRJ53.html)
[*]Save the file and exit gedit.
[*]```
sudo apt-get update
```
[*]```
sudo apt-get install mplayer-386 mplayer-fonts
```
[/LIST]

---

### Post by windbreaker13579 on 2005-11-07
mplayer is not in syamatic, or at least i cannot find it.... I am using Edubuntu...

---

### Post by windbreaker13579 on 2005-11-07
[QUOTE=bored2k][LIST=1]
[*]```
sudo gedit /etc/apt/sources.list
```
[*]Remove everything there and change it with these lines: [http://www.rafb.net/paste/results/dKHDRJ53.html](http://www.rafb.net/paste/results/dKHDRJ53.html)
[*]Save the file and exit gedit.
[*]sudo apt-get update
[*]sudo apt-get install mplayer-386 mplayer-fonts
[/LIST][/QUOTE]
 where do i type the code??

---

### Post by bored2k on 2005-11-07
In a terminal window.
Ubuntu: Applications --> Accesories --> Terminal or press Alt+F2 and type gnome-terminal
Kubuntu: Click on the Konsole button or press Alt+F2 and type konsole

---

### Post by Xian on 2005-11-07
In the wiki: [How-To Add Repositories in Synaptic](https://wiki.ubuntu.com/AddingRepositoriesHowto).

---

### Post by windbreaker13579 on 2005-11-07
ok it says

jedi@Jedi:~$ sudo apt-get update
E: Type 'http://www.rafb.net/paste/results/dKHDRJ53.html' is not known on line 1 in source list /etc/apt/sources.list
jedi@Jedi:~$  sudo apt-get install mplayer-386 mplayer-fonts
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what is wrong?

---

### Post by Cufishing on 2005-11-07
[QUOTE=windbreaker13579]ok it says

jedi@Jedi:~$ sudo apt-get update
E: Type 'http://www.rafb.net/paste/results/dKHDRJ53.html' is not known on line 1 in source list /etc/apt/sources.list
jedi@Jedi:~$  sudo apt-get install mplayer-386 mplayer-fonts
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what is wrong?[/QUOTE]
It would appear that the repositories are down at the moment.

---

### Post by windbreaker13579 on 2005-11-07
how would you fix the repositeries??

---

### Post by Cufishing on 2005-11-07
Not yours, the Ubuntu's are down.

---

### Post by windbreaker13579 on 2005-11-07
i wiped the entire  /etc/apt/sources.list and put [http://www.rafb.net/paste/results/dKHDRJ53.html](http://www.rafb.net/paste/results/dKHDRJ53.html)
in place of all the words...... is that bad.....  now when i run synaptic it says

Error
E: Type 'http://www.rafb.net/paste/results/dKHDRJ53.html' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

is that bad??

---

### Post by Cufishing on 2005-11-07
[QUOTE=windbreaker13579]i wiped the entire  /etc/apt/sources.list and put [http://www.rafb.net/paste/results/dKHDRJ53.html](http://www.rafb.net/paste/results/dKHDRJ53.html)
in place of all the words...... is that bad.....  now when i run synaptic it says

Error
E: Type 'http://www.rafb.net/paste/results/dKHDRJ53.html' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

is that bad??[/QUOTE]
Yes, this is bad.
You should copy just the text from that post. From the 1. to the e in the last word of universe on line 11.

---

### Post by Cufishing on 2005-11-07
[QUOTE=Kapre]windbreaker13579 - Mplayer is in Synaptic. Click on System----->Administration=====>Synaptic Package Manager ------>look for Mplayer. 

After seeing Mplayer --- Install it.

K[/QUOTE]
Hey guys, I'm not finding mplayer on Synaptic. Is there a down system somewhere?

---

### Post by Kapre on 2005-11-07
[QUOTE=windbreaker13579]i wiped the entire  /etc/apt/sources.list and put [http://www.rafb.net/paste/results/dKHDRJ53.html](http://www.rafb.net/paste/results/dKHDRJ53.html)
in place of all the words...... is that bad.....  now when i run synaptic it says

Error
E: Type 'http://www.rafb.net/paste/results/dKHDRJ53.html' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

is that bad??[/QUOTE]

Windbreaker - use this [thread]("http://www.psychocats.net/linux/sources.php") and scroll down on the page and look for the breezy 5.10 repositories. Better yet, copy the ones below and paste it to your sources.list

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

---

### Post by windbreaker13579 on 2005-11-07
ok... after i got 
sudo apt-get update 
to work but 
sudo apt-get install mplayer-386 mplayer-fonts
says
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what do i do?

---

### Post by Kapre on 2005-11-07
[QUOTE=windbreaker13579]ok... after i got 
sudo apt-get update 
to work but 
sudo apt-get install mplayer-386 mplayer-fonts
says
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what do i do?[/QUOTE]

Since you've upgraded your repo now, can you go in Synaptic PM and look for mplayer in the list? If its there, install it from Synaptic.

K

---

### Post by windbreaker13579 on 2005-11-07
ok.... THANKS!:smile:

---

