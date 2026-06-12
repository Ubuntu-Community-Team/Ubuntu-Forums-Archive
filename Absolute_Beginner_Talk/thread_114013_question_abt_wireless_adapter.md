---
title: "question abt wireless adapter"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by quiz_kwok on 2006-01-07
i am using a "airlink" wireless usb adapter, i find out that it only supports windows OS, is there any program or sth can make it works on Ubuntu?
thanks

---

### Post by danne on 2006-01-07
first install ndiswrapper-utils via synaptic:

sudo apt-get ndiswrapper-utils

then do the following in terminal:

cd /to/the/map/with/your/windows .inf and .sys driver file
sudo ndiswrapper -i .inf file
sudo modprobe ndiswrapper
sudo ndiswrapper -m

if everything worked fine you should see your card listed when you do:
sudo ndiswrapper -e

prolly your card is now listed in the network config under administration

byebye

check out the ndiswrapper wiki if you still have problems:cool:

---

