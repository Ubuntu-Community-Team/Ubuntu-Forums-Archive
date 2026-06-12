---
title: "Networking to a Windows 98SE computer"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Eric Weir on 2007-10-01
I am trying to network my new Ubuntu system and my old Windows system. I've installed a router, and both computers can reach the web through the router. I can see the Windows computer from the Ubuntu computer -- i.e., navigate the file system, copy files to the Ubuntu computer, etc., but I can't go the other way. 

I've gotten as far as getting the Windows computer to understand that it is on the network, but it doesn't know anything about the Ubuntu computer or the printer which is attached to it. I've asked the Windows computer to "find" the Ubuntu. It asks for the "name" of the computer it's to look for. I've given my user name -- eric -- and the host name that shows up under network settings -- eric-linux. It doesn't find anything under either name. 

I've thought about searching for the Ubuntu computer by it's IP address, but I'm not certain what that is. There are two IP addresses given under the hosts tab of network settings, one for "localhost," one for "eric-linux," but the numbers -- 127.0.0.1 and 127.0.1.1 respectively -- don't looking anything like the IP address for the Windows computer. 

Probably the wrong forum to be asking for help with a Windows computer but I don't know where else to ask. What do I need to do to get the Windows computer to recognize the Ubuntu computer? How do I determine the name and IP address of the Ubuntu computer?

Thanks in advance,

Thanks in advance,

---

### Post by mlentink on 2007-10-01
To find out the IP-adress of your Ubuntu-box, go to System > Administration > Network Tools

The first adress you'll see are probably for the loopback-interface (forget about that), but if you click on the drop-down arrow next to it, you'll  be able to see the configuration of eth0 or eth1 which probably lists an adress like 192.168.0.2 or something similar

Then you need to make sure the Ubuntu machine shows itself to the windows machine, for which you need to install Samba. Pls see the Wiki about installing that, there&#347; more there than I could tell you here.

---

### Post by Eric Weir on 2007-10-01
> **mlentink said:**
> Then you need to make sure the Ubuntu machine shows itself to the windows machine, for which you need to install Samba. Pls see the Wiki about installing that, there&#347; more there than I could tell you here.

Thank you for the other information, and for this, too. I was hoping to avoid it, but I guess I'll have to give it a try. 

When you say "Wiki" do you mean something here, i.e., Ubuntu specific, or Wikipedia itself?

Thanks, again

---

### Post by akiratheoni on 2007-10-01
> **Eric Weir said:**
> Thank you for the other information, and for this, too. I was hoping to avoid it, but I guess I'll have to give it a try. 

When you say "Wiki" do you mean something here, i.e., Ubuntu specific, or Wikipedia itself?

Thanks, again

[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

Or this one might help:

[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by Eric Weir on 2007-10-01
Thanks. I'll check them out.

---

### Post by Eric Weir on 2007-10-01
I checked Add/Remove Applications and found GSMBAD, described as an "easy to use GTK+ frontend for the Samba file and print server." 

Can I use it? Does it presuppose Samba? Will it install Samba?

Thanks,

---

### Post by mlentink on 2007-10-04
> **Eric Weir said:**
> Can I use it? Does it presuppose Samba? Will it install Samba?

Thanks,

I don't know the software. I'd have to try it first. But 'front-end' usually means the back-end (i.e. Samba) needs to be installed first.

---

### Post by Eric Weir on 2007-10-04
> **mlentink said:**
> I don't know the software. I'd have to try it first. But 'front-end' usually means the back-end (i.e. Samba) needs to be installed first.

I have downloaded and installed Samba -- although it's not showing up as installed in Add/Remove Applications! -- but at the moment I'm pursuing the possibility of getting the machines networked without using it. E.g., even before installing Samba, I could read the drives on the Windows machine from the Ubuntu machine. Windows Explorer displays the Ubuntu computer, though it won't let me access it. A techie friend has suggested a way of getting it to do so, which I'm about to try.

---

### Post by JKyleOKC on 2007-10-04
The problem you're having stems from a pair of facts: Linux knows about the FAT32 file system that Win98 uses, but Win98 does NOT know about the Ext3 file system that's used by Ubuntu. That's why your networking works only in one direction at the moment.

What Samba does is provide the translation between the various file systems, so that they can communicate. It's very easy to install in Xubuntu, which I'm using. Other flavors such as Ubuntu or Kubuntu are probably slightly different in the details. What I did was to pull up the applications menu, select the System category, and from there select Services. When it got to "Folder Sharing" I enabl3ed the service, at which time the system told me it would have to install either or both of two sharing services. Samba is one of the two. I selected it and let things move on from there. The program did the full installation for me, and I immediately had full communication.

Once it's working, you can then install the "SWAT" package to simplify tweaking the Samba configuration, but you may find that the initial defaults are adequate...

---

### Post by Eric Weir on 2007-10-04
> **JKyleOKC said:**
> What Samba does is provide the translation between the various file systems, so that they can communicate. It's very easy to install in Xubuntu, which I'm using. Other flavors such as Ubuntu or Kubuntu are probably slightly different in the details.

Thanks, Kyle. That's the clearest explanation of the problem I've heard. Also the simplest explanation of Samba installation I've encountered. Some are extremely complicated, at least for this newcomer, who hasn't gotten beyond highly tentative attempts at using the terminal. 

I does sound like Xubuntu has made the process a lot easier. There is no System category on Ubuntu's applications menu. I'll probe around and see if I can find some equivalent of the process you describe.

Or if anyone knows how to do what you described on an Ubuntu system, that would be cool, too.

Thanks again,

---

