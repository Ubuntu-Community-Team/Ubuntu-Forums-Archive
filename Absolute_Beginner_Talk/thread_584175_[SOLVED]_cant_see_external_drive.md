---
title: "[SOLVED] cant see external drive"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by ibbill on 2007-10-20
this is the error message I get when I try to open them

The volume uses the ntfs-3g file system which is not supported by your system.

I found this but it was in french crikey

[http://www.ntfs-3g.org/support.html#plugandplay](http://www.ntfs-3g.org/support.html#plugandplay)

---

### Post by Qwerty_ on 2007-10-20
Ok you are going to have to install NTFS-config which will enable your Ubuntu to beable to talk to NTFS formatted drives.

```
sudo apt-get install ntfs-config
```

Once you have installed it run ntfs-config with the following command.

```
sudo ntfs-config
```

Then select the option you want and you should be working :)

---

### Post by ibbill on 2007-10-20
OMG who are you people crikey:)  Worked like  a charm.WOW.

Well the way I see it I am 67 (older than dirt) and just started with linux Feisty and now Gutsy if I  can do this then anyone can.

 Of course with all the help we get here. (still not sure what planet you people are on) When I bite the bullet hope I go there lol.:guitar:

Thanks again Bill

---

### Post by Qwerty_ on 2007-10-20
Well ibbill I am glad to of helped you. Best of luck with the rest of your Ubuntuing. Anymore questions just feel free to ask here.

Oh btw we are on Mars :P

---

### Post by ibbill on 2007-10-20
lol one more question how do you make that box and insert the text tried to copy it no can do.

I know have more questions than a 4 year old.

---

### Post by Qwerty_ on 2007-10-20
You mean how sudo apt-get install ntfs-config is in a box.

you do with the code tag which is code inside of [].

---

### Post by Qwerty_ on 2007-10-20
Actually on a second read do you mean how can you paste into the terminal?

You have to copy the code then go into the terminal right click and click past ctrl+v wont work.

---

### Post by Jerry N on 2007-10-21
> **ibbill said:**
> OMG who are you people crikey:)  Worked like  a charm.WOW.

Well the way I see it I am 67 (older than dirt) and just started with linux Feisty and now Gutsy if I  can do this then anyone can.

 Of course with all the help we get here. (still not sure what planet you people are on) When I bite the bullet hope I go there lol.:guitar:

Thanks again Bill

67?  That ain't old!

Jerry

---

### Post by ibbill on 2007-10-21
Thanks Qwerty

Jerry N your right but it is a little old to be learning a new system. I must say I am smiling with pleasure since I switched over to linux.

---

### Post by Jerry N on 2007-10-21
I'm older than that and I have been fiddling with Linux (Ubuntu, LinuxMint, Linspire, Freespire, Puppy Linux, Damn Small Linux, Mandriva) for about 6 months.  Ubuntu seems to "feel" better than the others although Freespire sure is easy to get up and going.  With Gutsy Gibbon in place and set up the way I want it I plan to spend a little more time fiddling with Mandriva although I am not ready to give up Windows XP yet.  

Jerry

---

### Post by LLauranzonIII on 2007-10-21
living proof the old people can do it.;)

---

