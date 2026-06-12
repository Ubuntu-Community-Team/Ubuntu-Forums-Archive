---
title: "Can I use your server to netboot my box over the internet?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by TheoryBuilder on 2007-05-01
Hi,

  So, I should be right up front here, I haven't even installed Ubuntu yet.  However, I have installed other versions of Linux before and done some technical stuff.
  As I state in my heading, I am interested in fooling around with net boots.  I have noticed that most people do the following, they have *THEIR* own box and *their own* server and they use *THEIR* server to boot *THEIR* computer.  What I am interested in, is booting my box off of *YOUR *server.  Perhaps I don't know the ins and outs well enough,  but it occurs to me that there must be a server out there somewhere which I can configure my computer to "boot off of".
  I realize that there will be many, considerably technical aspects to even booting from my *own* server,  which I don't have because I don't even know how to configure a machine to *be* a server.  I don't even understand how computers connect to the internet.:)  :(  :)  :(   :)      :confused: 
  All that being said, I think it is fair for me to expect someone to be able to answer this basic Go/No-Go question:  Is it possible for me, using my own, local machine with 

a cable modem
a network card (and we'll say that it is pxe capable)
a hard drive (let's say it is formatted, ie completely blank, FAT32)
some ram
a CD rom drive
a usb port

to boot this machine, over the interenet using *someone's* server which exists and is ready right now, this minute (Monday April 1, 2007)? 

  Well, if my past experiences with bulletin boards still serves, I'm sure this will enrage a few people.
  Any help will be greatly appreciated.

     Ben


************************************************************************************
As the empire recedes like water flowing from a great vat, our small communities will appear like vortices amidst the turbulence.  Let the connections between those communities take the form of beautiful metaphors, rather than the plundering of Vikings.

************************************************************************************

---

### Post by dstew on 2007-05-01
In order to boot over a network, usually you have a computer with a ROM that can set up a simple ethernet network, and load the OS from a local server, using only the ethernet protocol. To get an OS from the internet, you would need to have TCP/IP running. I do not know of any ROM that does that.

However, if you are willing to run some disk-based software on your computer, the Grub boot loader has the abilitiy to set up TCP/IP and get an OS from the internet. See: [http://www.gnu.org/software/grub/manual/grub.html#Network](http://www.gnu.org/software/grub/manual/grub.html#Network)

I have not done this, but it seems possible. I do not know of a server that can supply the OS images.

---

