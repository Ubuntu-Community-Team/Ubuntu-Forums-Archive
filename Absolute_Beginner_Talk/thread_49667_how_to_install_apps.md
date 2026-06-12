---
title: "how to install apps"
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by porsher_puddles on 2005-07-17
this is my second day of having a go with ubuntu, i have downloaded xmms music player and burnt the unzipped files onto a cd, how do i install it i'm using ubuntu warty.
it all looks abit confusing at the moment.
i have managed to configure my internet and i can dial up but its so painfully slow but i have followed the instructions i was given but something is wrong, i am duel booting win me and that dials up and speed is good so something is wrong in ubuntu with my settings

---

### Post by varunus on 2005-07-17
Most software that you'll want to install, including XMMS, is available from Synaptic (System->Administration->Synaptic Package Manager).  Its a central repository for almost everything you could want.  However, if your net connection won't let you get packages well, you can download them manually from [http://packages.ubuntu.com/warty](http://packages.ubuntu.com/warty) and install them by opening a terminal and entering "sudo dpkg -i packagename.deb".  (For example, XMMS is available from that site.)

What modem do you have?  How did you set it up?

You may also want to consider upgrading to Hoary...though you will have to wait for the ShipIt CD's to come, as you probably don't want to to download Hoary.

---

### Post by Kvark on 2005-07-17
The normal way to install something is:
1. from the menues, open... System -> Administration -> Synaptic Package Manager
2. find the programs you want in the list (search for xmms)
3. mark the checkbox next to the programs you want
4. click apply
5. start using

To configure the package manager to find more programs..
[http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)

But make sure you replace all "hoary" with "warty" since that is your version.



If you are on dail up then you might want to install from CDs instead, which is more complicated and leads to dependancy issues and other problems.

if you have a .deb .rpm or .tar.gz file, you can try typing this in a terminal:
sudo alien --install /path/file

for example me installing xmms could be something like this:
sudo alien --install /home/kvark/newStuff/xmms.tar.gz

But there is no guarantees that alien or other offline methods will work or wheter or not it will lead to problems. The package manager really is the perfered way that  (almost) always works.



About the speed issue. Is it only firefox that is slow, or is downloads slow too?

---

### Post by porsher_puddles on 2005-07-17
it is not only firefox that is slow downloads are very slow to. on the same modem on the same machine when i swith to windows me i get 48.00 connection, when i'm try to use ubuntu web pages take minutes to load and on downloads i get 0.8 kbs compared to win me which runs at about 5.2 from the same download same website. i have followed the intrustions people have given me on here setting it up and it dials up no problems, just as slow as hell.

---

### Post by porsher_puddles on 2005-07-18
xmms is not on my list in the synaptic manager, but i did download it on my other computer, and put it unzipped on the unbuntu desktop in a folder i was hoping i could instal it from there but i can't work out how

---

