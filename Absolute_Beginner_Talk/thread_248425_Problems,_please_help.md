---
title: "Problems, please help"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Uncle_John on 2006-09-01
Hay:) 

I am quite new to ubuntu, but so far I found some problems:

- i can't sign my password in terminal
- i am learning python. Everytime i write a program in text editor i can't  run it in terminal. 

That's all for now:redface:

---

### Post by bodhi.zazen on 2006-09-01
Not sure what you mean by
> - i can't sign my password in terminal

for scripts; first:
```
chmod a+x <name_of_script>
```
Then run.

---

### Post by croak77 on 2006-09-01
What password? Your root (sudo) password? What are you doing in a terminal which doesn't recongize your password?

---

### Post by mcduck on 2006-09-01
> **Uncle_John said:**
> Hay:) 

I am quite new to ubuntu, but so far I found some problems:

- i can't sign my password in terminal
- i am learning python. Everytime i write a program in text editor i can't  run it in terminal. 

That's all for now:redface:

1. yes you can. When you're typing your password in teminal nothing is printed on screen so nobody standing behind your shoulder's will see what you are typing and how long your password is. Just type the password anyway and click enter and you'll see that it works :)

2. As already mentioned, you need to make that file executable. From commad line, chmod does that, I'd recommend 'chmod ug+x' that makes the file executable for owner and owner's groub, not everybody.

---

### Post by Uncle_John on 2006-09-01
sorry i see now i didn't describe well enough my problem

I downloaded cream IDLE for Python(cream_0.31cvs20041104_all.deb)
then i want to install it in terminal with sudo command:

 sudo dpkg -i cream_0.31cvs20041104-1_all.deb

then computer asks for password:

Password:
 
But i can't write anything, it is just like letters were invisible

(thanks for quick response:) )

---

### Post by Scorpuk on 2006-09-01
As bodhi.zazen said. The password is not displayed on the screen as you type it. This is a security measure.


Just type your password in when it asks for it and hit return. Make sure you use the password associated with the account that got added when you installed ubuntu.

---

### Post by Uncle_John on 2006-09-01
thanks for advice:redface: 
well i alredy have a new trouble

jar file is like zip file in windows, right?
well I extract a jar file and got new folder with installation
how do i install that program now?

---

### Post by 3rdalbum on 2006-09-01
A Jar file is not a general-purpose compressed archive. It is actually a program written in a language called Java.

I suggest you read the documentation on the program's website, for installation instructions. But generally, the .Jar file must be whole.

---

### Post by bodhi.zazen on 2006-09-01
> **Scorpuk said:**
> As bodhi.zazen said. The password is not displayed on the screen as you type it. This is a security measure.


Just type your password in when it asks for it and hit return. Make sure you use the password associated with the account that got added when you installed ubuntu.

Thank you, but it was mcduck that made the password suggestion.

mcduck is correct.

---

### Post by Uncle_John on 2006-09-02
yes i read the instructions, you need to have Java installed on your computer. I am downloading it right now. 

thanks for advice:)

---

### Post by Uncle_John on 2006-09-02
Hey, some problems with installing Java

I downloaded J2SE v 1.4.2_12  JRE from Java site to my desktop

Then I read instructions about installation. It found troubles at step two:

> 2. Make sure that execute permissions are set on the self-extracting binary.

    Run this command:
    chmod +x j2re-1_4_2_<version>-linux-i586.bin 

I run that command:

chmod +x j2re-1_4_2_12-linux-i586.bin

but then I got that:

chmod: cannot access `j2re-1_4_2_12-linux-i586.bin': No such file or directory

Does anyone have a clue what to do?

---

### Post by bodhi.zazen on 2006-09-02
Try
```
chmod **a+x** j2re-1_4_2_12-linux-i586.bin
```

May need to run j2re... as root(sudo)

---

### Post by Maylar on 2006-09-02
Where did you download the file to? Desktop? If so, it will not be in your /home when you first open the terminal. you have to type 
cd Desktop
and try the command again. Where ever you downloaded the file to, you need to change to that directory.

---

### Post by bodhi.zazen on 2006-09-02
> **Maylar said:**
> Where did you download the file to? Desktop? If so, it will not be in your /home when you first open the terminal. you have to type 
cd Desktop
and try the command again. Where ever you downloaded the file to, you need to change to that directory.

Good point.

That would be cd /home/user_name/Desktop.

I advise you create a directory in /usr or /home called "src" for such endevors.

---

### Post by Uncle_John on 2006-09-07
hey:p 

I still got problems. I wrote a small python program in text editor  - gedit
It's name is program1.py 

It is saved in my home directory

well when I want to run it, i put the icon of document in to the terminal.
I got that:

home/.../program1.py
bash: /home/.../program1.py: Permission denied

So I use sudo command ( i am not sure if i use it right) and write this:

 sudo  /home/.../program1.py
Password:
sudo: /home/.../program1.py: command not found

I can't see any letters when i write a password and flashing cursor is not  moving. But someoen said that's right so nobody can see your password, so I
guess that is right

But there is still a problem how to run python program.

Can anyone help?

---

### Post by bodhi.zazen on 2006-09-07
chmod a+x /home/user_name/program1.py

Run as a user (not sudo)
sudo error message because the file is not executible.

---

### Post by Uncle_John on 2006-09-14
hey=)

when i want to install some packages through terminal i write:

> sudo aptitude <packages>

then i am asked for password and i give it, but i get that:

> E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


What should that mean, how do i unlock that directory, which process is using it??

---

### Post by bodhi.zazen on 2006-09-14
Fyi command should be:

sudo aptitude install <program>

Are you running synaptic or update?

---

### Post by Uncle_John on 2006-09-15
Hey

Sorry a foolish mistake, but my problems don't stop here

Look I wanted to install some kind of music player so I could listen mp3s
I found that:

[http://www.ubuntuforums.org/showthread.php?t=186792](http://www.ubuntuforums.org/showthread.php?t=186792)

See SECOND STAGE

> sudo aptitude install gstreamer0.10-plugins-ugly mpg321 vorbis-tools gstreamer0.10-ffmpeg gstreamer0.10-gl libxine-main1 libxine-extracodecs gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll

I copy paste that in terminal and got:

 > sudo aptitude install gstreamer0.10-plugins-ugly mpg321  vorbis-tools gstreamer0.10-ffmpeg gstreamer0.10-gl libxine-main1 libxine-extrac odecs gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0. 10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll
Password:
Branje seznama paketov... Narejeno
Gradnja drevesa odvisnosti... Narejeno
Initializing package states... Narejeno
Building tag database... Narejeno
No candidate version found for gstreamer0.10-plugins-ugly
Couldn't find any package whose name or description matched "mpg321"
No candidate version found for gstreamer0.10-ffmpeg
Couldn't find any package whose name or description matched "gstreamer0.10-gl"
No candidate version found for libxine-extracodecs
No candidate version found for gstreamer0.10-plugins-bad
Couldn't find any package whose name or description matched "gstreamer0.10-plugi ns-bad-multiverse"
No candidate version found for gstreamer0.10-plugins-ugly
Couldn't find any package whose name or description matched "gstreamer0.10-plugi ns-ugly-multiverse"
Couldn't find any package whose name or description matched "gstreamer0.10-pitfd ll"
The following NEW packages will be automatically installed:
  libmodplug0c2 liboggflac3 libxvmc1
The following packages have been kept back:
  bind9-host dnsutils libbind9-0 libdns21 libisc11 libisccc0 libisccfg1
  libkrb53 liblwres9 libmagick9 libmysqlclient15off libssl0.9.8 libwmf0.2-7
  libxfont1 linux-image-2.6.15-26-386
  linux-restricted-modules-2.6.15-26-386 linux-restricted-modules-common
  mysql-common openssl xserver-xorg-core
The following NEW packages will be installed:
  libmodplug0c2 liboggflac3 libxine-main1 libxvmc1 vorbis-tools
0 packages upgraded, 5 newly installed, 0 to remove and 20 not upgraded.
Need to get 3183kB of archives. After unpacking 7995kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Narejeno
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libxine-main1 1.1.1+ubuntu 2-7.2 [2934kB]
Get:2 [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) dapper/main libmodplug0c2 1:0.7-5 [115kB]
Get:3 [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) dapper/main liboggflac3 1.1.2-3ubuntu1 [30,9k B]
Get:4 [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) dapper/main libxvmc1 2:1.0.1-0ubuntu4 [10,4kB ]
Get:5 [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) dapper/main vorbis-tools 1.1.1-3 [92,8kB]
Fetched 3183kB in 27s (117kB/s)
Selecting previously deselected package libmodplug0c2.
(Reading database ... 71297 files and directories currently installed.)
Unpacking libmodplug0c2 (from .../libmodplug0c2_1%3a0.7-5_i386.deb) ...
Selecting previously deselected package liboggflac3.
Unpacking liboggflac3 (from .../liboggflac3_1.1.2-3ubuntu1_i386.deb) ...
Selecting previously deselected package libxvmc1.
Unpacking libxvmc1 (from .../libxvmc1_2%3a1.0.1-0ubuntu4_i386.deb) ...
Selecting previously deselected package libxine-main1.
Unpacking libxine-main1 (from .../libxine-main1_1.1.1+ubuntu2-7.2_i386.deb) ...
Selecting previously deselected package vorbis-tools.
Unpacking vorbis-tools (from .../vorbis-tools_1.1.1-3_i386.deb) ...
Setting up libmodplug0c2 (0.7-5) ...

Setting up liboggflac3 (1.1.2-3ubuntu1) ...
Setting up libxvmc1 (1.0.1-0ubuntu4) ...
Setting up libxine-main1 (1.1.1+ubuntu2-7.2) ...

Setting up vorbis-tools (1.1.1-3) ...



To me it looks like something is missing, all those ugly and bad packages ?
I don't know, if anyone knows any better way to install mp3 player is very welcome:D  
In that case, is it recomended to delete these packages which were installed?

---

### Post by Uncle_John on 2006-09-15
I see that something is written in my language=)
short dictionary:

> Branje seznama paketov... Narejeno
Gradnja drevesa odvisnosti... Narejeno

means:

reading packages .... done
building tree structure ... done

hope you can help with that, if no please ask

---

### Post by 3rdalbum on 2006-09-15
You need to enable the Multiverse and Universe repositories.

Go to a terminal and type:

```
gksudo gedit /etc/apt/sources.list
```

Delete everything in there, and then paste the following in:

```

# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

Save your changes, and exit gEdit. In the terminal, type:

```
sudo apt-get update
```

Now you will have access to the repositories which contain the MP3 codecs, so the command you tried earlier will work (as long as you get rid of the words "libxine-main1" and "vorbis-tools" from the command, as they are already installed).

---

### Post by Uncle_John on 2006-09-15
thank you very much:D :D 

it finally works as it should

---

### Post by Uncle_John on 2006-11-06
Hello, have new problem:p 

I want to install my printer but I don't know how. I really don't have any time right now, but need printer as quick as possible. 

I have Epson stylus color 480

Can anyone help me?

---

### Post by Uncle_John on 2006-11-18
hey :D  
 
When I connect USB with computer I can't acces to it. I can see the icon in Nautilus, but when I click on it I get:

Unable to mount the selected drive
mount: Only the administrator can connect dev/sda1 to media/sda1

now, how can i can connect those two?

---

### Post by bodhi.zazen on 2006-11-19
It is likely a permissions problem.

What file system is on the USB ?

Assuming vfat, in a terminal unmount the usb drive and mount it with this:
```
mkdir /media/usb
mount /dev/sda1 /media/usb -o umask=000
```

You can also label your drive and add an entry in [fstab](http://ubuntuforums.org/showthread.php?t=283131)

---

