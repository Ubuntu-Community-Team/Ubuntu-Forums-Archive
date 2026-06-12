---
title: "Software Loading"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by MrRabbitC on 2006-01-16
If I just downloaded Mozilla Thunderbird and extracted the files from the .tar..
How do I load the program into Ubuntu? As of now, I just have the files extracted to a "Downloads" folder I created.

---

### Post by Gustav on 2006-01-16
Thunderbird is easely installed via the synaptic package manager or apt-get.

Either you can search for thunderbird in synaptic or you can type this in a terminal:
```
sudo apt-get install mozilla-thunderbird
```

---

### Post by heimo on 2006-01-16
[quote=MrRabbitC]If I just downloaded Mozilla Thunderbird and extracted the files from the .tar..
How do I load the program into Ubuntu? As of now, I just have the files extracted to a "Downloads" folder I created.[/quote]

Depends. But you most probably don't need to download and install this software on your own. You should use Synaptic Package Manager or apt-get to install it (it's called mozilla-thunderbird).
[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

On terminal window, you would type:
```
sudo apt-get install mozilla-thunderbird
```

---

### Post by MrRabbitC on 2006-01-16
Yep, I know you can get it that way. But I'm forcing myself to figure out how to download applications and intall them manually.
Say I had the downloaded .tar from Mozilla on my desktop and I extract the files to some other folder. Then what? (just using Mozilla as an example)

---

### Post by Gustav on 2006-01-16
It's different with different programs, but the most common thing is that it is a source tar.

If it is so then this way usually works:
```
tar xfvz <filename>.tar.gz
cd <newfolder_probably_named_the_same_as_the_file>
./configure
make
sudo make install
```
after the ./configure command you'll might have to install some libraries.

or you can use checkinstall instead of sudo make install and then get a .deb file that can be installed with
```
sudo dpkg -i <nameoffile>.deb
```
if you do it that way you can uninstall the program via synaptic or apt-get.

---

### Post by heimo on 2006-01-16
Very good advice, Gustav. :KS And I warmly recommend using checkinstall. :)

---

### Post by steve.horsley on 2006-01-16
In the case of firefox and thunderbird, they release a tar.gz file that just contains the precompiled binaries. The easiest thing to do is unzip the file where you want it. E.g. 
> cd /opt
sudo tar -xzf /home/me/downloads/whatever.tar.gz
This will create /opt/thunderbird, and you can run thunderbird with the command **/opt/thunderbird/thunderbird**. You can make a custom launcher on your desktop or on  a gnome panel. I also tend to link these from /usr/bin like this:
> sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird
so I can start them with the command **thunderbird.**
Actually, I tend to keep several different versions in /opt - thunderbird-1.5rc1, thunderbird1.5 etc. Then just link the latedt trusted version.

---

