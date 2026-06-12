---
title: "resolv.conf and DNS revert"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by pompeyjohn on 2005-11-10
Hi there,

I am having problems with my internet connection. The problem is DNS, but I dont know how to resolve it (I dont understand DNS), so any advice much appreciated.

My setup is as follows.

I have two machines, the first runs ubuntu, the second knoppmyth. They are both connected to a DLink 504t router which provides ADSL.

On the ubuntu box I can do a few things online (such as find cover art for amarok) but no surfing until I update my resolv.conf file with the following nameservers

194.72.9.39
197.74.65.68

These are the nameservers that British Telecom told me to use sometime ago - I think there are still valid.

Once I have updated resolv.conf with that info - I can surf the web wonderfully. The problem is that resolv.conf reverts back to 192.168.1.1 after about ten minute or so. (I expect the same things happens on the myth box but I have not looked into it yet)

The options I have on the router for DNS settings are:

In the DHCP settings page, DHCP server is enabled and the Primary DNS is 192.168.1.1

And in the DNS options page the preferred DNS server is set as 194.72.9.39 with the second as 197.74.65.68. There are the following relay selection options on this page:

Disable DNS relay
Use auto discovered DNS server only
Use User discovered DNS server only

I have looked into it, but something is just not making sense, and I am just becoming more confused. Can anyone advise the best settings?

Thanks in advance,

---

### Post by teaker1s on 2005-11-10
to set the static adress, use sudo ifconfig .... ( see the man page )
DNS edit /etc/resolv.conf

The interface showns up in the GUI network setting, but is not configured.
I think you have to click twice on it to configure it

---

### Post by pompeyjohn on 2005-11-10
Thanks for the reply. 

I looked at the man page, and ifconfig. I have also checked out the network settings gui tool (which I had not used before). The connection is there, and enabled - I didnt have to add anything new. The problem still is (I think) that the router is sending out a call every now again which changes the set nameservers in resolv.conf. I have tried disabling its DNS relay function but still the problem occurs.

This is getting really frustrating as I have to keep updating resolv.conf. I feel like there is something clear and obvious that I just cant see at the moment.

---

### Post by teaker1s on 2005-11-10
your not alone I have a static ip and manual dns settings all works fine until I reboot and then I have to manually select a location again in network settings for internet access.
I have a hunch that it could be the way ubuntu resolves ip address as it seems unable to use auto discover dns on the router like mac and xp can.
report it as a bug

---

### Post by ssam on 2005-11-10
have a check in system -> administration -> networking, check that 192.168.1.1 is not set as a dns server in there.

have a look at 
```
/etc/network/interfaces
```
check there is nothing defined there.

try running
```
sudo dhclient eth0
```
(replace eth0 with which ever interface you are running). this renews the dhcp information, and should update /etc/resolve.conf . it may give an error message if it cant do this.

also check the output of
```
ls -l /etc/resolv.conf
```
it should be a symbolic link to
```
/etc/resolvconf/run/resolv.conf
```
displayed as
```
lrwxrwxrwx  1 root root 31 2005-10-27 17:43 /etc/resolv.conf -> /etc/resolvconf/run/resolv.conf
```

i recently found that my resolve.conf was just a text file and dhclient would not update it.

if all else fails you could put your refered dns servers in resolve.conf and make it read only.

---

### Post by pompeyjohn on 2005-11-10
Thanks for the tips. A cat of /etc/network/interfaces has produced the following:

```
john@hooch:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
```

is that good ?! Um I am guessing it is not.

here is the result of the sudo dhclient eth0
```

john@hooch:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:13:20:b0:13:9a
Sending on   LPF/eth0/00:13:20:b0:13:9a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.5 -- renewal in 1622 seconds.
```

and here is the ls -l command

```
john@hooch:~$ ls -l /etc/resolv.conf
-rw-r--r--  1 root root 23 2005-11-10 21:05 /etc/resolv.conf
```

I am not sure what I am looking for here - but that means there is no symbolic link right??

---

### Post by ssam on 2005-11-10
the output of /etc/network/interfaces looks fine

the symlink is not there.

ok can you give the output of
```
cat /etc/resolvconf/run/resolv.conf
```
just to check, (we dont want to make a symlink to a non existant file)

---

### Post by pompeyjohn on 2005-11-10
```

john@hooch:~$ cat /etc/resolvconf/run/resolv.conf
cat: /etc/resolvconf/run/resolv.conf: No such file or directory

```

ahhh ha!! so there is no file!! how do I fix this?

Thanks again for all the help

---

### Post by ssam on 2005-11-10
ok, thats slightly odd, i think.

as a quick fix i suggest that you hardwire the dns servers into /etc/resolv.conf as long as these address will stay the same then you should be ok.

```
sudo gedit /etc/resolv.conf
```

and put in

```

nameserver 194.72.9.39
nameserver 197.74.65.68

```

and save it.

then run
```
sudo -w /etc/resolv.conf
```
to lock it.

if you ever need to unlock it run
```
sudo u+w /etc/resolv.conf
```

---

### Post by pompeyjohn on 2005-11-10
[QUOTE=ssam]ok, thats slightly odd, i think.[/QUOTE]

Yep, agreed :) 

I have tried to lock the file using the syntax you suggested but I get the following error

```
sudo -W /etc/resolv.conf
sudo: illegal option `-W'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
```

Thanks for all your help

---

### Post by ssam on 2005-11-10
oops sorry, my bad

```
sudo chmod -w /etc/resolv.conf
```

likewise

```
sudo chmod u+w /etc/resolv.conf
```
to unlock

---

### Post by pompeyjohn on 2005-11-10
AAARRRGHHHH !!!](*,) 

Even with the file locked it still reverts back to 192.168.1.1

---

### Post by janne5011 on 2005-11-10
hi dont know if this helps but  have a similar setup,my router ip=192.168.0.10 and this works for me:
.................................
interfacefile:

# The primary network interface
iface eth0 inet dhcp

auto eth0
.............................
resolve.conf-file:
nameserver 192.168.0.10
...............................................

In adninstration-->network -->dnsserver set: 192.168.0.10
becuase the router then handle dns there is no need use the dns you got from ISP as I understand it,any way it works:)

---

### Post by pompeyjohn on 2005-11-10
ok, I think I have found a fix. I hope this works for you as it is currently working for me:

(thanks to all for help and suggestions - much appreciated)

Once the nameservers are set in resolv.conf, edit ...

/etc/dhcp3/dhclient-script 

... and comment out like this:

```
#make_resolv_conf() {
# if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
# local new_resolv_conf=/etc/resolv.conf.dhclient-new
# rm -f $new_resolv_conf
#
# if [ -n "$new_domain_name" ]; then
# echo search $new_domain_name >> $new_resolv_conf
# else # keep 'old' search/domain scope
# egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# if [ -n "$new_domain_name_servers" ]; then
# for nameserver in $new_domain_name_servers; do
# echo nameserver $nameserver >>$new_resolv_conf
# done
# else # keep 'old' nameservers
# egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# chown --reference=/etc/resolv.conf $new_resolv_conf
# chmod --reference=/etc/resolv.conf $new_resolv_conf
# mv $new_resolv_conf /etc/resolv.conf
# fi
#}
```

It appears to be working for me. Hope that helps :)

---

### Post by chanorange on 2005-11-11
> **pompeyjohn]ok, I think I have found a fix. I hope this works for you as it is currently working for me:

(thanks to all for help and suggestions - much appreciated)

Once the nameservers are set in resolv.conf, edit ...

/etc/dhcp3/dhclient-script 

... and comment out like this:

```
#make_resolv_conf() {
# if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ] said:**
> ; then
# echo search $new_domain_name >> $new_resolv_conf
# else # keep 'old' search/domain scope
# egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# if [ -n "$new_domain_name_servers" ]; then
# for nameserver in $new_domain_name_servers; do
# echo nameserver $nameserver >>$new_resolv_conf
# done
# else # keep 'old' nameservers
# egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# chown --reference=/etc/resolv.conf $new_resolv_conf
# chmod --reference=/etc/resolv.conf $new_resolv_conf
# mv $new_resolv_conf /etc/resolv.conf
# fi
#}
```

It appears to be working for me. Hope that helps :)

Sorry for being a newbie but im having the same problem as you and im not sure what you have done above? Have you edited out that part of the file? (cause mine looks the same) Have you changed it?

Ive tried so many things to stop my DNS reverting back to 192.168.1.1 its driving me mad.

---

### Post by pompeyjohn on 2005-11-12
[QUOTE=chanorange]Sorry for being a newbie but im having the same problem as you and im not sure what you have done above? Have you edited out that part of the file? (cause mine looks the same) Have you changed it?

Ive tried so many things to stop my DNS reverting back to 192.168.1.1 its driving me mad.[/QUOTE]

No worries dude! I am happy to (try and) help :D

The way I have edited the file is to load it as the super user in a program called gedit. The command for this was 

sudo gedit /etc/dhcp3/dhclient-script

A line that is commented out starts with a #. So what you need to do is find the section in your file that starts with 

make_resolv_conf() { 

and add # to each line underneath it until you get to a line saying  

fi
}

These are like the end bits of the sections. comment these out as well, and you'll have stopped that section from loading. This should stop resolv.conf over writing to 192.168.1.1. 

I know how frustrating that is!!! I hope this helps. I would have replied sooner but I was at work. I'll be online all evening now, so give me a shout if i can help in any way.

Best of luck,

---

### Post by t2kburl on 2005-11-20
this should be a sticky or something

excellent information here

I was on the verge of dumping ubuntu because of the snail pace of surfing

Thank you

---

### Post by jizackson on 2006-01-04
I think a cleaner solution would be to edit your dhclient.conf and add the following lines:

interface "<interface>" {
  supersede domain-name-servers <domain-name-server(s)>;
}

where <interface> is the interface that's hooked to your router, and <domain-name-server(s)> are the domain server(s) you want to default to (multiple servers here should be separated by commas).

For more information see the man file for "dhclient.conf".

---

### Post by patholio on 2006-01-04
Hi, i had exactly the same trouble with my (almost identical down the them make and model of router) setup, i found that thist thread solved my woe
[http://www.ubuntuforums.org/showthread.php?t=39606&highlight=slow+internet+resolv.conf](http://www.ubuntuforums.org/showthread.php?t=39606&highlight=slow+internet+resolv.conf)
i just followed the instructions, and it worked :)

---

### Post by Koobi on 2006-01-04
i used to have this problem, but i found the fix somewhere on the net...i think it was this forum....well anyway, this is what i did:

```

sudo apt-get install resolvconf
sudo apt-get install pump
sudo apt-get install dnsmasq

```

once i installed all of those, i had to enter the right values into my resolv.conf and then deactivate my network and reactivate it again and i havent had this problem since then.

give it a go and let me know how it goes :)


hope this helped

---

### Post by stream303 on 2006-01-23
> Once I have updated resolv.conf with that info - I can surf the web wonderfully. The problem is that resolv.conf reverts back to 192.168.1.1 after about ten minute or so. (I expect the same things happens on the myth box but I have not looked into it yet)

No problem since you know what the dns addresses of your isp really are.  Problem is that dhclient is picking up the dns server inside your router every time your lease gets renewed rather than using your isp's dns servers.

To fix this, edit your **/etc/dhcp3/dhclient.conf** file
(sudo gedit /etc/dhcp3/dhclient.conf)

Just before the request line, add:
[B]prepend domain-name-servers 123.45.678.90, 123.45.678.91;
[/B]

Using your real nameservers of course.  Just separate with a comma, and don't forget the semicolon at the end.  This will force your resolv.conf file to be written using your real nameservers.

Now you can bring the interface down and up again with the terminal to make this change take effect:

sudo ifdown eth0
sudo ifup eth0

If you go back into your network settings gui, you may want to doublecheck your DNS settings and perhaps add things like Search Domains, ie

yourisp.net

---

### Post by ardchoille on 2006-01-23
[QUOTE=ssam]oops sorry, my bad

```
sudo chmod -w /etc/resolv.conf
```

likewise

```
sudo chmod u+w /etc/resolv.conf
```
to unlock[/QUOTE]
that does not lock the file, root will still be able to write to it - root can override chmod settings. To lock a file so that even root cannot write to it:

```

sudo chattr +i filename

```

then root will not be able to modify it. To unlock the file again:

```

sudo chattr -i filename

```

then the file can be written to again.

---

### Post by jimrz on 2006-01-23
try a lower case 'w', rather than 'W'...think that is case sensative

---

### Post by ardchoille on 2006-01-24
[QUOTE=jimrz]try a lower case 'w', rather than 'W'...think that is case sensative[/QUOTE]
it doesn't matter whether you use a "w" or a "W", root can still write to a file even if it is -r--r--r-- . To prove this, do the following:

```

sudo echo hi > /root/newfile

```
This creates a new file called "newfile" in /root with the content of "hi".

```

sudo chmod 444 newfile

```
This makes the file read only to all users including root.

```

sudo ls -l /root/newfile

```
Check that /root/newfile is actually read only (-r--r--r--).

```

sudo rm /root/newfile

```
This deletes the supposed read only file.

```

sudo ls -l /root/newfile

```
Is the file still there? What happened is that root deleted a read only file. If that file had truly been read only, root wouldn't have been able to delete it.


The only way that I know of to make a file impervious to change is to do:
```

sudo chattr +i filename

```
That makes the file read only to all, including root.

---

### Post by LordYama on 2006-02-07
After running a system update, I found that resolvconf was installed and that my static IP would no longer access the Internet. /etc/resolv.conf was empty apart from the "DO NOT EDIT THIS FILE BY HAND" warning.

After some poking around, I found my original settings in /etc/resolvconf/resolv.conf.d/original. The solution was simple:

```
$ sudo cp /etc/resolvconf/resolv.conf.d/original /etc/resolvconf/resolv.conf.d/base
$ sudo resolvconf -u
```

If /etc/resolvconf/resolv.conf.d/original does not exist, enter your settings into /etc/resolvconf/resolv.conf.d/base manually and then run resolvconf -u.

---

### Post by fieldyweb on 2006-03-07
I thought i had solved my problem there, but i also get the same... 

sudo -w /etc/resolv.conf

Output as yourself...

---

### Post by jamesr on 2006-03-07
If I am reading your first posting correctly 
> The options I have on the router for DNS settings are:

In the DHCP settings page, DHCP server is enabled and the Primary DNS is 192.168.1.1

And in the DNS options page the preferred DNS server is set as 194.72.9.39 with the second as 197.74.65.68. There are the following relay selection options on this page:


This are the options for your router setup or did I interpretate that incorrectly. I would  have thought that the Primary DNS should 194.72.9.39 because every time the router renews the lease  it will pickup the information from the router.

just my 2p's worth

---

### Post by mzilhao on 2006-03-08
hi,

i'm having the same problem. my resolv.conf file keeps getting updated every time i boot! the solution given isn't working for me, probably because i'm not using DHCP, it is static. 
so... how can i keep that damn resolv.conf file from getting updated? when i tried ```
sudo chattr +i resolv.conf 
```
it just said:
```
@ubuntu:~$ sudo chattr +i /etc/resolv.conf
chattr: Inappropriate ioctl for device while reading flags on /etc/resolv.conf

```
any ideas...?

thanks,
Miguel

---

