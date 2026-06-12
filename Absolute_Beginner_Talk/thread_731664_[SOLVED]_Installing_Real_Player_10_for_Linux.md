---
title: "[SOLVED] Installing Real Player 10 for Linux"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-22
hello,

I've got Helix installed (on Ubuntu Gutsy) and I tried listening to a radio station. A message popped up suggesting that Helix doesn't have the capacity for playing bla bla bla, so I clicked ok and the page [http://www.real.com/linux](http://www.real.com/linux) opened. 

Now, can you please tell me what I should do to install Linux 10? If I click on "download real player" a .bin file gets saved on my home folder, and I don't know how to handle it (wine emulator doesn't respond for some reason). If I click on "advanced installation: RedHat Package" the archive manager tells me it cannot handle the file...

thanks.

---

### Post by StOoZ on 2008-03-22
first make the .bin file executable by doing this:
sudo chmod +x <file name.bin>
then run ti
./file name.bin

int our case its:
sudo chmod +x RealPlayer10Gold.bin
then
./RealPlayer10Gold.bin

I might wrote the filename incorrectly,insert the correct filename

---

### Post by reyhan on 2008-03-22
try this download the file in here [COLOR="Red"][http://www.soft32.com/Download/Free/RealPlayer/4-122615-1.html]("http://www.soft32.com/Download/Free/RealPlayer/4-122615-1.html")[/COLOR]

go to the directory where the RealPlayer10GOLD.bin file is stored
and type this on terminal 
```
sudo chmod +x RealPlayer10GOLD.bin.
```

and install it by this

```
sudo ./RealPlayer10GOLD.bin.
```

and you must change the owner the directory in to yours

```
sudo chown yourusername:yourusername -Rh /home/yourusername/RealPlayer
```

i hope thats work

if that doesn't work go to this link [[COLOR="Red"]http://www.ubuntux.org/insatalling-real-player[/COLOR]]("http://www.ubuntux.org/insatalling-real-player")

---

### Post by al.adab on 2008-03-22
thanks for your reply!

The extraction works. That's what I get: 

[I]Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/daniel/RealPlayer]: [/I]

Any idea? What shall I do now?...

---

### Post by reyhan on 2008-03-22
its where do you want to install the real player directory i install it on /home/myusername/realplayer

---

### Post by al.adab on 2008-03-22
It worked, thanks so much. Just...where is Real Player? I mean, it's not in the start menu...or is it just Helix upgraded?

---

### Post by reyhan on 2008-03-22
try this go to the System>preferences>main menu 
and click the Sound & Video and click the New item

Type:application
Name:RealPlayer 10
Command:realplay
Comment:RealNetworks' open source media player

and the icon is in the directory you install
real player it is in the share folder the file name is realplay.png

i hope thats work

---

### Post by al.adab on 2008-03-22
there's something wrong with the command. I tried both "realplay" and "realplayer" and I get the following message: 

"could not launch menu item / failed to execute child process / "realplay" : no such file or directory"

any idea?

---

### Post by al.adab on 2008-03-22
figured it out :) instead of writing "realplay" at command, you need to browse for "realplay" and double-click on it. the command line will look like: /home/xxxx/RealPlayer/realplay

---

### Post by reyhan on 2008-03-22
okey

---

### Post by beebelo on 2008-03-24
I am doing this as well, and I understand the instructions, but my question is:  

Why would one install an *application* in one's /home/~ directory?  Isn't this kind of thing supposed to be installed in /usr/local/ if it doesn't go through Synaptic or apt?

But that raises another question in my mind:  
If it's installed in /usr/local, then what directory?  

Please explain. Thanks.

---

### Post by Darganot on 2008-03-24
> **beebelo said:**
> I am doing this as well, and I understand the instructions, but my question is:  

Why would one install an *application* in one's /home/~ directory?  Isn't this kind of thing supposed to be installed in /usr/local/ if it doesn't go through Synaptic or apt?

But that raises another question in my mind:  
If it's installed in /usr/local, then what directory?  

Please explain. Thanks.


You install applications to your /home/username directory for 2 reasons:

1) so you don't have to run the installer as root
2) so the program doesn't get wiped out with a reinstall if you're using a separate /home partition

I'm not sure that i understand the rest of your question but if you run an installer normally (as root) it puts it in pre-set directories kind of like a windoze installer...I personally couldn't tell you all the places the files go.

---

### Post by beebelo on 2008-03-24
Thanks for the reply.  

From my very limited knowledge, apps that are installed manually are supposed to end up in /usr/local/ for the same reasons you mentioned (and traditionally, /usr/local/ should be on a separate partition).  But I almost never used it because everything I need I can get through apt.  You'll see several sets of bin and sbin directories in your system, and that's where the executables end up.  

My problem is that I know "just enough to be dangerous" :)

---

### Post by beebelo on 2008-03-24
Anyway, I installed it to the default directory and it's working just fine!

---

