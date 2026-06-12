---
title: "Ubuntu Problem#3"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by hellmet on 2006-05-05
I am on an Intel 915 GAV.
I got the MOBO when Intel was NOT
integrating their Lan Card on the MOBO.
So I had to buy an ethernet card.
I have an Realtek 8139D Card.
This stupid card does not get identified
during install.
When i type
**sudo pppoeconf**
it says..
[B]no ethernet interface found
Wud u like Modconf to add card(s)[/B]
or something similar to that.

I say 'yes'..and I get an error 
"Modconf not recognised/installed"

I am presently typing from my Windows..
So i don't remember the exact lines.

Please help people...
I was actually planning to get on Ubuntu from today.
I had got my Free cds yesterday.
But now I am stuck everywhere.


P.S::Please don't recommend buying a new card.
They mite be cheap..but I can't afford them right now.

---

### Post by deadgobby on 2006-05-05
[QUOTE=hellemt]I am on an Intel 915 GAV.
I got the MOBO when Intel was NOT
integrating their Lan Card on the MOBO.
So I had to buy an ethernet card.
I have an Realtek 8139D Card.
This stupid card does not get identified
during install.
When i type
**sudo pppoeconf**
it says..
[B]no ethernet interface found
Wud u like Modconf to add card(s)[/B]
or something similar to that.

I say 'yes'..and I get an error 
"Modconf not recognised/installed"

I am presently typing from my Windows..
So i don't remember the exact lines.

Please help people...
I was actually planning to get on Ubuntu from today.
I had got my Free cds yesterday.
But now I am stuck everywhere.


P.S::Please don't recommend buying a new card.
They mite be cheap..but I can't afford them right now.[/QUOTE]

[https://wiki.ubuntu.com/WLANHowto?highlight=%28lan%29](https://wiki.ubuntu.com/WLANHowto?highlight=%28lan%29)
[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

Have you tried the links above?

---

### Post by hellmet on 2006-05-05
I said Ethernet...not Wlan or WIFI..dude...
My card is not being detected.
I wanted to know how to install it using 
the drivers that the Card manu. gave me.

---

### Post by skippy81 on 2006-05-05
Can you duel boot with windows on your machine? If you can then you boot into windows and retrieve the driver for the network card.  It's name will end with .inf.  

The driver for the card will originally come in a .exe package.   That is useless, you need the .inf file.  Use device manager in windows to find out what the driver name is, and then track that driver down.

Once you have the driver .inf file, you need to download ndiswrapper-utils and ndisgtk packages. Since I assume you cant access the web while running linux you will have to copy them across from another machine.  

[http://archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.5-1ubuntu1_all.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.5-1ubuntu1_all.deb")

[32bit ndiswrapper]("http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.1-4ubuntu2_i386.deb")

OK you should now have 3 files.  2 .deb packages and 1 .inf driver. 

Copy all 3 files to your home folder in ubuntu.

From a terminal type > sudo dpkg -i *.deb you MUST be in your home folder when you do this.  If it doesnt work, leave out the "sudo".

Once the packages are installed type the following from a terminal:

> sudo ndisgtk

Yes, it does say "Wireless" at the top, but it should still get your card working with a bit of luck.

Click install new driver, and attempt to load your windows .inf driver.

Let me know if you make any progress - if this doesn't work you will need to try a different approach.  

There is a linux driver here: [http://www.ovislink.com/newovislink/drivers.asp]("http://www.ovislink.com/newovislink/drivers.asp") but to use it you would need to install the kernel headers, GCC 3.4 and fiddle around with a makefile, so try the ndiswrapper method first.

---

### Post by hellmet on 2006-05-05
Thanks a lot for that patient reply skippy.
I did what u said.
I get this
"ntslnt"
"Hardware Present?:NO"


ntslnt is the .inf i use for windows xp.

I dunno wats wrong.

You said there is another way around..
Could you please enlighten me on the same??
You explained the above thing beautifully..

-hellmet

---

### Post by hellmet on 2006-05-05
This is what is written in the ReadMe  for  the "linux" driver 
provided with the Card.

I cud not understand too much of it.
Can someone throw some lite on it.
Or if  u have a better option please lemme
know.I HAVE to get my Ubuntu connection running.

Help me Please!!!

---

### Post by skippy81 on 2006-05-05
OK, the next approach is to try out a linux driver for your card I found.  Download the package from here:

[http://www.ovislink.com/newovislink/products/adapters/OV-8139D/linux24x-8139cp(101).zip]("http://www.ovislink.com/newovislink/products/adapters/OV-8139D/linux24x-8139cp(101).zip")

On top of this you will also need to install GCC3.4 and the Linux kernel headers.  This will enable you turn the C code supplied with the linux driver into a module which can be loaded into your kernel.

Once again you will have to download some files. Here they are:-

[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb")
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb")
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb")
[http://archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1-2ubuntu6_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1-2ubuntu6_i386.deb")

Ok, copy the driver and the 4 files over to your ubuntu PC.  Make a folder in your home directory with a name like "GCC" and copy the 4 .deb files into it.  Copy the linux driver and makefile directly into your home directory.

Open a terminal.  Type in the following: > cd GCC/
 sudo dpkg -i *.deb 

Ok the packages you downloaded should install.  If they don't, then try taking them out and installing them one-at-a-time with the above terminal syntax.  Close the terminal when finished.  Now the 4 .deb files are installed we can install the kernel headers.  

Insert your installation CD for ubuntu (not the live CD) and open a terminal. Type: > aptitude
You can use the 'aptitude' program to get the kernel headers from the disc. Navigate through the menu "Not Installed Packages > devel > main" Find the entry titled linux-headers-i386 or something similar.   Click your mouse where it says "Package" at the top of the window and select "Install".  Then press G a couple of times and it should install the kernel headers for you.  

I will add the rest of the instructions in a minute

---

### Post by skippy81 on 2006-05-05
OK I didnt realise you had a disc with drivers on it.  Extract those ones to the home directory, dont worry about the ones that I found on the internet just yet.  

Now I need you to look through the files you extracted.  You should have a makefile there.  I need you to copy and paste its contents in to the forum and I will try and adapt it for you to make it work.  Make it quick 'cause im sleepy :D

While im doing that you can get on with installing GCC3.4 and the kenel headers as per my instructions.

---

### Post by hellmet on 2006-05-05
[http://www.megaupload.com/?d=Y048Q344](http://www.megaupload.com/?d=Y048Q344)

here it is...
thnks for stayin awake:D

---

### Post by hellmet on 2006-05-05
Rite now in India its 2:30 in the noon>>>>
he he...
wat time is it for u ??

---

### Post by skippy81 on 2006-05-05
I'm UK so it's actually 10am hehe. I been writing an essay all night.  Right, im sorry but these drivers you've linked won't compile, neither will any of the other ones I've managed to find.  

I will have a look into this later, but I'm afraid I dont have any time left tonight.  The problem appears to be that we are in version 2.6 of the kenrnel now, all these drivers are for 2.4.  I would recommend you check google and see if you can come up with a newer driver.  

Sorry we cant get this done now.

---

### Post by hellmet on 2006-05-05
here is a .c version of the driver for my card.
Just rename the .txt file to .rar and unzip.

---

### Post by hellmet on 2006-05-05
Hey Skippy,
u know wat..
i found the driver for 8139D in the uncompiled form.
I dunno wat I shud do with this
I am just attaching this here..
Please help me further...dude..
Thanks buddy...

-hellmet

---

### Post by skippy81 on 2006-05-05
Im afraid that driver is still a really old one.

Can you open a terminal please and type:

> lspci

copy and paste the output to the forum please.

Do the same with:

> dmesg

I think that ubuntu should support your card without additional drivers.  Did the card work for you under windows?

---

### Post by hellmet on 2006-05-06
Yaa skippy,it worked like a charm, under windows...
anyway here I have attached the LSPCI and DMESG output
file...
its a document in Ubuntu.
remove  .txt   and open....  (no file extension).
thnx..

---

### Post by skippy81 on 2006-05-06
Funny thing is your card *should* get recognised.  The only compatable drivers I can find are the ones which are included with the kernel.  We will try forcably loading them.

As a last ditch effort have a go at doing:

> sudo modprobe 8139too

in a terminal window.  

Check your network settings under gnome and see if a card becomes visible.  

You can remove that module with either
> sudo modprobe -r 8139too
 > sudo rmmod 8139too sorry im not sure which is the best way, im not much of an expert.

and then have a go with > sudo modprobe 8139cp

Make sure you try both these mods, you want to only have one of them running at a time.  I guess you could try running both together if your desperate :razz: You can check if they are loaded with > lsmod.

If this doesnt work then have another fiddle with the windows driver and ndiswrapper method we discussed earlier.  

If all this fails, I seriously recommend you get a new card.  Your brand of card is very unusual - it is virtually unheard of while the rest of the 8139 series are fairly common.  A network card is reasonably cheap, but is also the most time consuming thing to have problems with in linux since it denies you access to the net.

---

### Post by hellmet on 2006-05-06
this is wat i got ...when i loaded both the drivers..and did
**lsmod | grep 8139**

8139cp                 18432  0
8139too                23552  0
mii                     5248  2 8139cp,8139too


wat the heck does tat mean??

---

### Post by hellmet on 2006-05-07
any help coming ??

---

### Post by skippy81 on 2006-05-07
All those codes mean is that the module has loaded.  Whether or not it makes the ethernet card work is another thing entirely.

You need to test to see if the system is recognising the card.  

> ifconfig
ifconfig eth0 up

etc

---

### Post by hellmet on 2006-05-07
Nope dude.
Read this thread..
[http://www.linuxquestions.org/questions/showthread.php?t=391215&highlight=8139D](http://www.linuxquestions.org/questions/showthread.php?t=391215&highlight=8139D)
I got the Driver 8139too.c
I need someone to compile that for me.
I dunno how to compile KERNEL MODULES

PLEASE SEE ATTACHMENT
UNZIP.Change TXT to .C
Thnkx

---

### Post by skippy81 on 2006-05-07
The problem is the driver you have provided is an older version of the driver which comes with the linux kernel.  You allready have the most up to date 8139too module you can get.  I find it hard to believe that adding one line of text into the source code of the module will make it work, if this was the case then the kernel team would have allready done it.  

What version of the linux kernel are you currently running? Do a -

> uname - r

---

### Post by hellmet on 2006-05-07
Is there any way to reverse engineer an object file and 
get its source code??
Then it'd be possible to add that one line to it.
I'll tell u my version of kernel.
I am in windows currently

---

