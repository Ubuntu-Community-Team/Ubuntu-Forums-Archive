---
title: "Sharing files between Macbook + Ubuntu over a wireless network: Howto"
date: 2008-05-13
forum: Apple Hardware Users
---

### Post by django0909 on 2008-05-13
I've just spent forever trying to work out a quick and easy way to do this, and eventually came across this. I have an Ubuntu based desktop which is wired into a linksys router and to the outside world. I also have a Macbook which connects to said router. I was trying to work out a nice, simple, newbie-esque way to transfer files between both desktops and eventually came up with this, which I'd like to share with others.

First I installed openssh-server on the Ubuntu box, 

```
sudo apt-get install openssh-server
```

Then got hold of my IP address for my Ubuntu machine,

```
ifconfig
```

Usually 192.168.xx.xx

Then I installed a program called Fugu on my Macbook, (freeware), which you can get anywhere but I got mine here:

[http://www.columbia.edu/acis/software/fugu/]("http://www.columbia.edu/acis/software/fugu/")

Then all I did was get Fugu installed, and add the following info:

Connect to: <ip_address_of_ubuntu_box>
Username: <username_on_ubuntu_box>

The password it asks for after you hit connect is the one you're logged into the Ubuntu session with.

And voila, you get both desktops on your Mac and can transfer files back and forth quickly and easily. Takes 2 seconds to set up and is very, very good.

As a bonus, if you turn on Remote Access on your Macbook, (under 'Sharing), you can do Places-> Connect to Server on your Ubuntu box and after filling in your Macbook details, (gained in the same way via terminal commands on the Mac), you get the reverse setup.

It's invaluable to me now and I just wanted to share it with someone in the hope it becomes useful :)

---

### Post by ssam on 2008-05-15
you can also try gshare on linux. it is in the repos.

it has an FTP server, and advertises it using zeroconf. the shares should show up on mac on the network folder (though in mac os 10.3 i had trouble connecting using the finder, though cyberduck work).

---

### Post by bzzzzz on 2008-08-22
This is way cool, and by far the easiest way of sharing that I've found.

I'd like to thank the guy but I can't see the little icon - oh well thanks anyway.

The only thing that I was unsure of was the ip address.  Mine came up under the heading eth1 inet addr:

NOT Bcast

---

### Post by cyberdork33 on 2008-08-22
This is called SFTP. Basically you are using FTP over a ssh connection. You can also get to a shell on your linux machine using the same thing.

Open Terminal on your Mac
Type 'ssh ubuntuusername@192.168.x.x'
You will get prompted for a password
then you will get to a terminal prompt, but this is the remote machine. you can edit files, move and delete things, install applications, etc.

 (and actually you can do all this the other way too. OS X has an ssh server included. it is called 'remote login' under the sharing area of system preferences.) I use Filezilla on Ubuntu to connect to sftp.

---

