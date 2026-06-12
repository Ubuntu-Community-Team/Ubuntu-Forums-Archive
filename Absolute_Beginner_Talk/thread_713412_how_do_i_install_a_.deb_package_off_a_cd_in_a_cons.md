---
title: "how do i install a .deb package off a cd in a console?"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by cpu_medic on 2008-03-02
ok so i have installed ubuntu on my desktop with an ati radeon x1650, and my video doesnt work, nor does screwing with xorg. so i looked into it deeper and i found envy. ok cool, i dont have internet connected to my desktop yet, however i do on my laptop (when i go to the coffee shop.) so i downloaded envy and burnt it to a cd, and now im stuck. i dont know how to install a .deb off a cd (commands) in the console. cus thats all i got right now. I NEED EHLP PLEASE

---

### Post by tdrusk on 2008-03-02
```
cd /media
```
Type
```
ls
```
to list your options
```
cd cdrom
```
(if cdrom is the option)
```
ls
```
to see the files on the cd
```
sudo dkpg -i *name of package*.deb
```

Rock on.

---

### Post by cpu_medic on 2008-03-02
i tried it and it sees cdrom0 and cdrom1 i have tried the "ls" command and nothing happens to ether of them. am i doing something wrong?

i have typed in "cd /media/cdrom(1 and 0) ls

---

### Post by neurostu on 2008-03-02
the easiest way will be to copy the .deb from the cd rom to your desktop using the gui.

Then open a terminal and then type:
```

cd Desktop
sudo dpkg -i <package.deb>

```

---

### Post by cpu_medic on 2008-03-02
i dont have a gui
i have a console...and thats it untill i can install envy for my video card.

---

### Post by neurostu on 2008-03-02
So where you able to find cdrom1 and cdrom0? Are both directories empty?  Maybe your CD isn't getting mounted correctly.  

You might want to check out this page:
[http://linux.about.com/od/linux101/l/blnewbie4_2_2.htm](http://linux.about.com/od/linux101/l/blnewbie4_2_2.htm)

---

### Post by seventhc on 2008-03-02
you might want to try
```
cd /media/cdrom0
```or```
cd /media/cdrom1
```one of those should work. :)
Edit: oh..never mind..I just saw that you said you tried that. I didn't notice that before.

---

### Post by seventhc on 2008-03-02
you say when you tried that nothing happens..but it would either give an error or your prompt would change to something like
j0hn@cipher:/media/cdrom0$  #this is how mine looks
so what does it do or say?

---

### Post by tdrusk on 2008-03-02
> **cpu_medic said:**
> i tried it and it sees cdrom0 and cdrom1 i have tried the "ls" command and nothing happens to ether of them. am i doing something wrong?

i have typed in "cd /media/cdrom(1 and 0) ls

wait wait wait.

did you type
```
cd /media/cdrom*1/0*
```
(press enter)
```
ls
```
to see the files?

'm just trying to rule out all possible problems...

Are you sure the cd has the .deb file on it?

Try taking out the C.D. and putting it back in, or even loading a different C.D. and do what I did previously.

---

### Post by tdrusk on 2008-03-02
Double Post

---

### Post by oldos2er on 2008-03-02
Is your cd-rom drive mounted? "sudo mount /dev/cdrom /media/cdrom0" should do it.

---

