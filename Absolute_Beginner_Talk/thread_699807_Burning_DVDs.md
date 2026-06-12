---
title: "Burning DVDs"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-02-17
im tring to create a ISO image from my DVD and i cant figgure out how to work devede can any help, how do i point it to the DVD any help would be great TY

---

### Post by zerhacke on 2008-02-17
cat /dev/scd0 > /home/yourusername/dvd.iso

You might have to change the /dev/scd0 to your dvd device.

---

### Post by articwolf939 on 2008-02-17
do i do that under the title or the file box? cause they both have a  add button

and how or where do i change the device to my DVD drive

---

### Post by wolfen69 on 2008-02-17
what zerhacke means is, open terminal and:
```
cat /dev/scd0 > /home/yourusername/dvd.iso
```
i havnt tried this myself, but that is what he means.

---

### Post by articwolf939 on 2008-02-17
i tried it but it says this 
$ cat /dev/scd0 > /home/yourusername/dvd.iso
bash: /home/yourusername/dvd.iso: No such file or directory

can anyone else help or have ideas?

---

### Post by tanman on 2008-02-17
You could also just use a program like K9 copy or DVD95, they are both in add/remove.
They will just make a copy of the disk and then create a ISO of it.

---

### Post by tanman on 2008-02-17
Also DeVeDe, which is a great program, only works with video files that you want to turn to a DVD.

---

### Post by articwolf939 on 2008-02-17
ive tried k9copy and maybe it just me and im dumb but i couldn't figure out k9 either :-\
i know there no hope for me lol

---

### Post by tanman on 2008-02-17
What could you not figure out? I will try to help you. Also give DVD95 a shot also.

---

### Post by articwolf939 on 2008-02-17
ok well let say i open k9 and i have a dvd in my drive how do i get k9 to see the dvd

[IMG]http://tinypic.com/view.php?pic=2nks7mc&s=3[/IMG]


sry it took so long

---

### Post by articwolf939 on 2008-02-17
[http://tinypic.com/view.php?pic=2nks7mc&s=3](http://tinypic.com/view.php?pic=2nks7mc&s=3)

screen shot

---

### Post by mc4man on 2008-02-17
just click on the little folder icon  to load the dvd. Then you can make your choices as to what you want to copy
Make sure you have libdvdcss2 installed as per the advice on your other thread

---

### Post by tanman on 2008-02-17
When you click on the folder like the previous post stated it should open up your CD/DVD drive. The items on the disk should then be listed below.
Check what ones you want and then click the DVD buttom up top and select where you want the image saved.

---

### Post by articwolf939 on 2008-02-17
ok i think i have it thank you for all your help knowing my ill have a prob burning lol

---

