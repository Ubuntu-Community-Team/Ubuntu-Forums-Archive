---
title: "&quot;make&quot; ??"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by Phili on 2006-03-20
Hello,
I'm an absolute beginner with linux and ubuntu.

I want to install a driver and the readme says that i should install it using "make" how does that work?

could you please explain it step by step?

Thanks

---

### Post by Brunellus on 2006-03-20
back up and tell us what you're trying to install.

---

### Post by taurus on 2006-03-20
If you plan to install a program from source, you need to build it.  Normally, you can achieve that with 
```

./configure
make
sudo make install

```
Of course, always read the README and INSTALL that come with the software you intend to build...

And for Ubuntu, you need to install build-essential first before you can compile anything so do this from a terminal.
```

sudo apt-get install build-essential

```

---

### Post by Phili on 2006-03-20
@taurus

sorry, but where do I enter that?

It's a driver for my wireless lan modem

---

### Post by saphil on 2006-03-20
[SIZE=2]In my experience, 
1. open a terminal window.  
2. [/SIZE][SIZE=2]navigate to the folder in which the files you are attempting to install reside, e.g. /home/your_profile/Desktop/new_thing by entering:[/SIZE]
[SIZE=3]cd /home/your_profile/Desktop/new_thing [/SIZE] 
[SIZE=2]3. switch to root by entering 
[SIZE=3]su - and the password
[SIZE=2]4. check the folder contents to see if there is a shell script called Configure if so enter[/SIZE]
 ./Configure
[SIZE=2]This sets up the makefile so it will install based on your system environment. Read the output carefully to make sure it worked, and you are not looking at confusing error messages.
5. just type:
[/SIZE] make
[SIZE=2]and hit [enter] The system will give you feedback if the make command needs more arguments or options, or it may just whir away and compile the files for you. 
6.  In some cases the next step is to type 
[SIZE=3]make install[/SIZE]
which will put the compiled files where they are supposed to be in the file system. If this step is not required, there will be feedback to that effect.

If you cannot make sense of the response **Configure or make** gives you, you can copy them to this forum thread for clarification.
[/SIZE][/SIZE][/SIZE]

---

### Post by Brunellus on 2006-03-20
[QUOTE=Phili]@taurus

sorry, but where do I enter that?

It's a driver for my wireless lan modem[/QUOTE]
which driver, which wlan adaptor, which chipset?

It could be that there are easier ways of doing this.

---

### Post by jjf on 2006-03-20
Phili,

I gather from your responses that you're brand new.  Welcome.  :)

As Brunellus said, people here are very willing to help you get your wireless drivers installed and there may be easier ways of achieving that.  But if you're interested in installing software from source (which is what you're trying to do here), here are some quick tips:

1- These commands need to be typed into a terminal window (looks like the old DOS command prompts).  You can access this by going to your **Applications** menu, then selecting **Accessories**, then **Terminal**.

2- My n00b brain has wrapped itself around installing from source this way:

 * **./configure ** tells the installer to configure itself for the specific settings of your machine
 * **make** tells Ubuntu to "make" an install package that you're going to use in just a minute
 * **sudo make install** tells Ubuntu to install that package you just "make'd".  The "sudo" on the front means "superuser do."  It's like telling Ubuntu, "I'm smarter than you think I am and I know what I'm doing, so let me do this action that you've restricted for normal users."

---

### Post by Phili on 2006-03-20
It's the ZyXel ZyAir B-220 USB Wlan receiver

I don't know the chipset, I'll google it later

and yes, I've never used anything else than windows and I only installed ubuntu yesterday

---

### Post by Phili on 2006-03-20
i just tried to install it and when i have to enter my password after "su", it doesn´t work, nothing happens

---

### Post by Princey on 2006-03-20
[QUOTE=Phili]i just tried to install it and when i have to enter my password after "su", it doesn´t work, nothing happens[/QUOTE]


Nothing will happen unless you press enter. That's how linux is by design especially Ubuntu. Once you're at the root prompt (su) and it asks for password, type in the password you use to log on to the computer. Nothing will show, but don't worry. It's just a security measure. Press enter when you're done typing and everything should run thereafter.

---

### Post by pbaehr on 2006-03-20
I'm pretty sure you can't use su without enabling the root account which Ubuntu has disabled by default. I wouldn't recommend doing that, especially if you're new to Linux. I THINK
```
sudo -i
``` will have the same effect as using su.

For more information on sudo, check this out: [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by engla on 2006-03-20
[QUOTE=Phili]i just tried to install it and when i have to enter my password after "su", it doesn´t work, nothing happens[/QUOTE]
su takes the root password, but there is no need to enable the root user. The equivalent thing that takes **your** password is 'sudo', use that instead. jjf has written down the instructions using that variant.

---

### Post by Phili on 2006-03-20
same problem here:

if i press a key, there´s simply no single change, no  ***´s, nothing
of course if i press enter it says that the password is incorrect because i didn´t enter anything.

i guess my installation is broken :mad:

---

### Post by pbaehr on 2006-03-20
Linux does not show *s or anything. When you type the password nothing will show up. Just do it blindly and then press enter.

A lot of new users are concerned that no masked characters show up when they type. That's just not how it happens in Linux. You'll get used to it.

---

### Post by Phili on 2006-03-20
passwork worked, however the installation not

edit: i moved to the directory of the extracted driver and did make config as it´s written in the read me but it didn´t work

---

### Post by Shane11 on 2006-03-20
I'm not trying to hijack this thread but....
I too am having trouble installing a wirelss dongle (Belkin with rt2570 chipset).
I've managed to untar the driver to the correct folder, but can't get 'make' to work either.

Everything I read points me to Synaptic, but of course that wants to connect to the internet and it can't because I haven't configured the dongle yet!!! 
I understand I need to install build essentials but keep coming up against the fact that I can't find 'em! Are they on the install cd, and if so how do I use apt-cd to get them.

I read one post that suggested there was a 'Basic Development Stub' in Synaptic - blowed if I can find it!! 

If any one can explain this very slowly, in english words, i'll be gratefull!

Regards Shane.

---

### Post by Phili on 2006-03-20
well lets hope for help eh? ;)

---

### Post by Brunellus on 2006-03-20
if you absolutely *must* compile from source, you must first install the build-essential package using apt or synaptic.  I prefer apt:

sudo apt-get install build-essential

then it's the usual
./configure
make
make install

---

### Post by Phili on 2006-03-21
you say "must", is there any other way to install it?

---

### Post by saphil on 2006-03-21
there are a few packages that come as packagename.deb which is a native debian install  package.  They are easier.  You just open a terminal window and type in 

sudo dpkg -i /path/to/packagename.deb [enter]

it kicks back a password prompt, so you type in your regular user password [enter]
and it does its stuff.

---

### Post by Phili on 2006-03-22
I'm about to get mad :mad: 

I've been using windows for years, i never had stupid problems like this! I'm about to throw all this ubuntu crap away :( 

I did: 
make config normally-no result
make config in the su directory-no result
make config in the sudo-i directory-no result
make config in the extracted folder directory-no result

I tried every installing program in linux but it didn't help!!!!

I attached the file I need to install, anybody please explain step by step (!!!) how to do it...

---

### Post by wsanders on 2006-03-22
OK, first: have you done "sudo apt-get install build-essential" (without the quotes) in a terminal window? If so, then you can navigate into the director you extracted the file to. Open a terminal and type "cd [and then whatever directory you extracted the file to]". If you haven't extracted the file, go to wherever you downloaded it to (probably your desktop, "cd ~/Desktop ") and then type "tar -xvvf linux-wlanng-0.2.3.tar.gz " Then, you'll need to type "cd linux-wlanng-0.2.3" . in that folder, type " ./configure " . After that is done, type "make" and then type "sudo make install" and then enter your password.

---

### Post by Phili on 2006-03-22
ok it worked nearly completely, thank you very much.

It now asks me for the linux source directory.
what is it? I´m using the current AMD64 ubuntu version

---

### Post by Phili on 2006-03-22
nobody?

---

### Post by Phili on 2006-03-25
:-|

---

### Post by Shane11 on 2006-03-25
You'd think some one would have responded wouldn't you !
I still haven't got very far. I took a different route and installed my Speedtouch 330 modem - that took nearly a week to get on line!
Finally managed that this morning. Phew.
So I can finally get the 'build-essential' files on board.


The next plan is to get the wireless RT2570 working now, sounds simple, but somehow I think it'll take me another week.

I hope you post back if you get yours working.

---

### Post by Phili on 2006-03-25
the only possibility i have to connect to the internet is my wireless lan modem...

---

### Post by DarkN00b on 2006-09-12
I got my Zyxel B-220 working!

First, go [here]("http://oase.uci.ru.nl/~bradaa/nerdnotes.org/index.php/category/nerdnotes/linux/") and scroll down to "E-Tech Wireless USB Adapter and Linux".

Basically, the guy says to install the firmware as normal, then open a terminal window and navigate to the directory where you downloaded the firmware then type (still in Terminal):

```
sudo cp *fw /lib/firmware/`uname -r`
```

Type it _exactly_ like that. In fact -- copy that and paste it into Terminal and hit enter.  As soon as I did, my B-220 lit up and started searching for a connection.

Now.  Open System->Administration->Networking.  You should see a new connection called "Wireless Connection".

Now...
1. Click the new connection and then click the Properties button.
2. Enter your WLan's ESSID under "Network name (ESSID):" ****This is case sensitive!****
3. Click OK and you should be connected after the changes are made to the connection.

**This worked for me.  My wireless ZyXEL B-220 is now working!**

---

