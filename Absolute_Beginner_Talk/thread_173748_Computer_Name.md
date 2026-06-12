---
title: "Computer Name????"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-05-10
How do I name my computer on Ubuntu?  I have a small network setup at home and  when I go to see who is on my network, (you know when you log on to your router and check the DHCP Table), I don't see the names of my linux computers.  Is there a way that I can name my linux computer?:confused:

---

### Post by hardXcore on 2006-05-10
when you first install?

---

### Post by macdo on 2006-05-10
Create a file /etc/hostname and type your computer name into it.

I'll check, but I'm pretty sure that's how I did it...

---

### Post by NeoGreen on 2006-05-10
I checked under /etc/ directory and it stated that there was already a hostname file.  How do I us vi to modify the file and input my computer name on it?  I know that I have to type i to input but I do not now what else to type when I am done.:confused:

---

### Post by adssse on 2006-05-10
I believe all you would have to do (after typing 'i' for insert mode) is to type in your new hostname in place of whatever it was, hit the <esc> key to enter command mode and than type the colon key and wq (you should see this in the bottom left hand corner) and than type enter. This should save it (thats what the 'w' is for and quit vi, what the 'q' is for. You can verify the file is changed by typeing 'cat hostname' in the terminal to display it.

I am not sure, but I noticed that the hostname is also specified in the first line of the hosts file, not sure if it needs to be changed there also.

EDIT:
I also just noticed if you feel more comfortable in a gui, you can go System->Administration->Networking and than click on the general tab. From there you can change the hostname. (Not sure if this is the correct way to do what you want, I was just looking.)

---

### Post by harisund on 2006-05-10
Ok, if I am correct, host name is not what you are looking for at all. 

If you just type "hostname" on a terminal, it will tell you your machine name. 

However, if you are looking at a DHCP table and want to see a name, you will have to manually edit a file. 

Do in your terminal "gksudo gedit /etc/dhcp3/dhclient.conf". It will ask you for your password. Enter it and gedit opens with the appropriate file. 

Look for a line that goes ```
#send host-name "andare.fugue.com";
``` Remove the '#' that is at the beginning of the line. This shows that it is a comment and the machine will ignore it. It won't ignore if you remove the '#'

Then inplace of the andare.fugue.com type in whatever you want to see on the DHCP table. Remember to still enclose it with double quotes and remember to end it with a semi colon (basically just edit andare.fugue.com) 

Then either reboot your computer, or open a terminal and simply do ```
sudo dhclient -r
sudo dhclient eth0
```
and you should be able to see it in your dhcp client table. (I am assuming eth0 is your card. You can substitute appropriately). IF you don't know then don't bother, simply reboot.

---

### Post by joshrobinson on 2006-05-10
system >administration > networking
click general tab
set the hostname

---

### Post by harisund on 2006-05-10
joshrobinson and macdo, I don't think the parent poster is having problems with the hostname. What he is having problems with is his DHCP client not sending the hostname to the DHCP server, which it doesn't by default. 
> you know when you log on to your router and check the DHCP Table)
This is not a hostname error of any sort, it more of a peculiar feature of dhclient, the default DHCP client application on Ubuntu

---

### Post by joshrobinson on 2006-05-10
[QUOTE=harisund]joshrobinson and macdo, I don't think the parent poster is having problems with the hostname. What he is having problems with is his DHCP client not sending the hostname to the DHCP server, which it doesn't by default. 

This is not a hostname error of any sort, it more of a peculiar feature of dhclient, the default DHCP client application on Ubuntu[/QUOTE]

maybe i read over it too fast, i saw "computer name" and how do i name my computer so thats what i replied

your ip address's dont show up in your router table? in my router the names ususally dont show up with linux i have to name them by ip or mac address on the router setup page

---

### Post by harisund on 2006-05-10
[QUOTE=joshrobinson]
 in my router the names ususally dont show up with linux i have to name them by ip or mac address on the router setup page[/QUOTE]

Yes. I wonder if that's a bug or a feature. By default in Linux (or atleast in Ubuntu) they don't show up! 

If you want something to show up, you will have to edit /etc/dhcp3/dhclient.conf like I mentioned in my earlier post. 

I think it's more of a problem with the 'dhclient' program. If you use some other DHCP client (MEPIS etc use a program called 'pump' unlike Ubuntu) then they automatically show up in the router settings

---

### Post by NeoGreen on 2006-05-15
Okay I'll try it, buy yes you were right.  What I want it to do is to show up on my DHCP Table on my router.

---

