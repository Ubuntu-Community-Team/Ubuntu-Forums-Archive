---
title: "apt-get error"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by bluezapper on 2007-03-14
Hi,

I get the following error message when I try to use 

apt-get install update or any other apt-get.... command

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


How can I remove it or why is it caused,


best regards,

bluezapper

---

### Post by AtrejuT on 2007-03-14
do you by any chance have synaptic running at the same time? Then you have to close that before using apt-get

---

### Post by bluezapper on 2007-03-14
sorry, solved the problem

my synaptic package manager was open and I was executing apt command.

thanks

bluezapper

---

### Post by NikoC on 2007-03-14
I'm not sure, but maybe you could try:
sudo apt-get install packagename

Which will ask you for your pass just one time.

Edit: nevermind, you guys already replied while I was still typing ;)

---

### Post by fanny on 2007-03-14
maybe you need to add extra repositories follow the instruction on this link.(i had the same problem) [http://ubuntulinuxhowto.blogspot.com/2006/06/how-to-add-extra-repositories.html](http://ubuntulinuxhowto.blogspot.com/2006/06/how-to-add-extra-repositories.html)

---

