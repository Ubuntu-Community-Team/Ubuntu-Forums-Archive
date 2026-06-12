---
title: "nery frustating to download libraries for every ubuntu pc"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by shashank on 2006-09-25
How Can I Have A Backup Of Archives I Have Downloaded And Use Them Somehow
In Every Ubuntu Pcs ...

For Example I Downloaded Xine Plyaer Which Downloaded 5 Files Frm Intenrnet
An 3 Frm Cd.
To Install It I Have Thought Of 2 Methods In A New Ubuntu Installed Pc.......
1)copy Those 8 Files In Archive Folder (it Is Aomwehere In /usr/archives It May Be Wrong! )
And Then Use Apt Install Command
2) Create A Shell Script To Install These Files Along Which Ill Keep With These Files In A Seperate Folder For Every Application I Want To Install

---

### Post by ubuntuuser on 2006-09-25
Packages are usually saved in the /var/cache/apt/archive directory until you delete the cache.

I'm not on a linux PC right now, so maybe this is not the exact location, but it's somewhere around this path.

---

### Post by seshomaru samma on 2006-09-25
yes /var/cache/apt/archives

---

### Post by bluefrog on 2006-09-25
install apt-proxy (universe) on one of your computer.

install new computer. point apt-get sources.list to your apt-proxy computer.

James

---

### Post by IanW on 2006-09-25
I guess there's some way of burning the contents of that directory to disc in a format which will work with Synaptics "Add CDRom" option?

---

### Post by shashank on 2006-09-25
u know there is a menu editor in accesories..............
i added archive manager through that
it shows all the archives which i downloaded .and in that archive manager u can browse for downloaded files
so it means those files can be copied in ay where even in windows directory
which i can write on a cd from nero
and then later using archive manger i can browse to cdrom and install them i guess
ill do this experiment tomorrow and post a reply if it would be successfull!!!!!!!!!!!!!!!!!!!!!!!!!!:)

---

### Post by lamego on 2006-09-25
You could try apt on cd:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

