---
title: "How do I make Ubuntu Edgy faster? And my internet?"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Malik on 2007-03-11
Im new to linux. just installed yesterday with my HD partioned to have windows on the other side. Btw anyway I can make ubuntu's HD bigger? I made it so windows has 108gigs but i wanted it to have more like 50 so linux could have more.

---

### Post by sgorovyy on 2007-03-11
You can try the program qtparted
to install it go to Applications -> Add/Remove -> then you can just type in search qtparted and then install this program. It allows you to repartition your disk. After you install it you need to run it for this go to terminal and type
sudo qtparted
it needs to be run by an admin user to allow to repartition your drives.
Then choose your HD in the list and you see the partitions you have. Now you can change them as you want to. after that press commit changes and it will do what you want.

---

### Post by astrolabio on 2007-03-11
Some thing i know to make it faster:

1) Install a optimized kernel for your processor
sudo apt-get install linux-686
then reboot
2) Install your video card drivers
3) Install AND
sudo apt-get install and
4) Find a tutorial about prelink and use it

---

