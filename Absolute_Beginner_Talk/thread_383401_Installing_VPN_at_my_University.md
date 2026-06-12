---
title: "Installing VPN at my University"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by tralfmordian on 2007-03-13
Hello. I' very new to Linux and Ubuntu, so bear with me. I go to a University where the wifi is accessed through a vpn client. In my old windows machine, there was a cisco vpn client that pretty much installed itself, where I could put in my pwd and students id, etc, and it would log on. On the University's website for their wifi, they have clients for windows and mac, and also one for Linux, but they note:
"Linux command-line version 4.6.00.0045 
This client is unsupported but is known to be in use on campus."
Basically meaning that I can download this thing, but they won't help me with it.

So I've downloaded it (a tar.gz) file, and I was able to extract it all to a folder on my desktop.

I know nothing about how to install things except through synaptics and/or package manager, and all that I find in this new folder are scripts and executables that don't seem to be doing anything when I try to run them. 

Can anyone help me understand how to install this in a way that I can use it? I have tried to look through the forums some, but I'm not even sure what the right terminology would be for this. If I search for things like "installing," I just get a lot of threads devoted to installing Ubuntu, or using synaptics...

Thanks!

---

### Post by apjone on 2007-03-13
have a look at 

[http://www.cutlersoftware.com/ubuntuinstall/#source](http://www.cutlersoftware.com/ubuntuinstall/#source)

You'll get the hang of it!

---

### Post by apjone on 2007-03-13
Basically op a terminal 

cd Desktop
tar -xvzf package.tar.gz
cd package
./configure
make
sudo make install

thats the basics

---

### Post by dstew on 2007-03-13
I connect to my work NT server using VPN and Samba. You do have to install the VPN client as mentioned in the link posted by apjone. Make sure you have the compiler tools installed before you try to compile the VPN client:

> To proceed you must have the compiler tools installed. They all come with the package build-essential, available in Synaptic.

After the VPN client is installed, you need to start it and connect using the command line in the terminal. Read the documentation that comes with the VPN client. I might be able to help you with getting connected once you have VPN installed.

---

### Post by tralfmordian on 2007-03-13
> **apjone said:**
> Basically op a terminal 

cd Desktop
tar -xvzf package.tar.gz
cd package
./configure
make
sudo make install

thats the basics

I've never felt so dumb. The file is extracted to a folder on my desktop. I've gone to that directory in a terminal, and I type "./configure" and it tells me 
"bash: ./configure: No such file or directory"

I'm sure this means something very obvious to everyone, but I have no idea what that means, other than the fact that my computer doesn't like that command...

I have no idea what it means, even after reading through the tutorial linked above, and looking around for help with the command. I want to be able to not only get this working, but also understand what and how I end up doing it, but it seems hard for me to find a good starting place...?

---

### Post by dstew on 2007-03-13
Do you see the configure file in the package directory?

---

### Post by r4e on 2007-03-13
I could be wrong about this, but I don't think 4.6 needs to be compiled from source. Cisco's installation directions should help get you on the right track:

[http://www.cisco.com/univercd/cc/td/doc/product/vpn/client/4_6/uglinsol/vcugls2.htm](http://www.cisco.com/univercd/cc/td/doc/product/vpn/client/4_6/uglinsol/vcugls2.htm)

Just keep in mind that for the Ubuntu distribution the init scripts are stored in /etc/init.d (not /etc/rc.d/init.d).

So according to their instructions, these commands should work:

```

tar -xvzf vpnclient-linux*.tar.gz 
cd vpnclient
su -c './vpn_install'
su -c '/etc/init.d/vpnclient_init start'
su -c 'cp **university**.pcf /etc/CiscoSystemsVPNClient/Profiles'
su -c 'vpnclient connect **university**'

```

You probably will be able to get away with just going with the defaults after executing command 3 above. I just used the defaults for installing Cisco VPN Client 4.8 on Edgy.

In the last two commands substitute **university** with the name of the pcf file your university provided.

I hope this helps--please let me know if it works.

You might find this page useful too:

[http://www.cisco.com/univercd/cc/td/doc/product/vpn/client/4_6/uglinsol/index.htm](http://www.cisco.com/univercd/cc/td/doc/product/vpn/client/4_6/uglinsol/index.htm)

---

