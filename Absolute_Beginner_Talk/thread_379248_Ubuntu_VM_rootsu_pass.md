---
title: "Ubuntu VM root/su pass?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by EnigmaStigma on 2007-03-07
I'm running a VM of Unbuntu, trying to kill two birds with one stone. I was wondering if anyone knows how to access the root login on the VM offered through VMware's website.

Also as a side question:
I was hopping to check out the IRC channels for Unbuntu and was wondering if anyone knew the server address. I searched the Unbuntu IRC page but couldn't find the address there.

Thanks,

Enigma

---

### Post by EnigmaStigma on 2007-03-08
RE-Post: Posted in the weehours of the morning but got no reply. Hope it's alright if I re-post.

I'm runing a Ubuntu VM and can't seem to find out how to get root access or su access anywhere. Some say the password is VMware, vmware,VMWare, or Ubuntu, but none of those seem to work.  I'm in class for Linux right now, learning about the shadow file, passwd file, etc. Unfortunantely without root or su access I can't even view the shadow file. 

I was also wondering about some of the edits and additions people have made their own Ubuntus that were helpful to them. I'm not really doing anything with it other than class work but I know that since I'm getting into a field where it's good to know Linux it's not a bad idea to get as familiar as possible with it. Of course I wanna be able to help others out to. 

Thank you,

Enigma

---

### Post by docetes on 2007-03-08
where did u download the virtual machine image?

---

### Post by etank on 2007-03-08
> I was wondering if anyone knows how to access the root login on the VM offered through VMware's website.
I'm not sure what you mean by this. Ubuntu's root account is disabled by default.

> I was hopping to check out the IRC channels for Unbuntu and was wondering if anyone knew the server address. I searched the Unbuntu IRC page but couldn't find the address there.

There are many irc channels for Ubuntu. Using an irc client (XCaht, Gaim, irssi) connect to irc.freenode.net on port 8001. Then you should be able to join the channels. This link has a list of all (or most) of the Ubuntu related channels. [https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

---

### Post by EnigmaStigma on 2007-03-08
I downloaded it from VM's site at [http://www.vmware.com/vmtn/appliances/directory/693](http://www.vmware.com/vmtn/appliances/directory/693).

---

### Post by EnigmaStigma on 2007-03-08
sorry about the shotty description and thanks for the reply. I did re-post since I didn't think anyone would have answered. There's a better description here [http://www.ubuntuforums.org/showthread.php?p=2265436#post2265436](http://www.ubuntuforums.org/showthread.php?p=2265436#post2265436)

---

### Post by docetes on 2007-03-08
can u log in at all?

---

### Post by EnigmaStigma on 2007-03-08
I can get in as a regular user, in fact I don't even have the option to login when the Ubuntu Vm fires up. and if I log out of the user I have a total of 10 seconds to log in as a different user or the ubuntu user will fire up automatically.

Thanks man,

Enigma

---

### Post by jkeyes0 on 2007-03-08
According to that site, the "regular user" is ubuntu, with a password of "ubuntu". With that account, you should be able to "sudo", which means "super user do". Instead of using su, you can type sudo before a command, and it will run it as root. This is a security feature of Ubuntu.

By the way, the password it will ask for when you sudo something is the same as the user password, ubuntu.

---

### Post by bapoumba on 2007-03-08
@ EnigmaStigma: other thread merged.

---

### Post by EnigmaStigma on 2007-03-08
> **bapoumba said:**
> @ EnigmaStigma: other thread merged.

Thanks. Was getting a little confused for a second there.

And thanks JKeyes0. I had read at a few other places that was the thing to do but I thought that the were simply talking about su and not something totally seperate. Thanks man. I'll try it out when I get back home.

---

