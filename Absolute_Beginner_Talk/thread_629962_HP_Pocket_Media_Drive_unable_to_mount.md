---
title: "HP Pocket Media Drive unable to mount"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2007-12-02
Hi All, 

Some time ago, my pocket drive was in a windows machine, and was not removed safely. Now, it does not mount at all in Ubuntu. No issues in windows still, I can use it on any other windows machine, but I cant use it on Ubuntu, as it says there was an unclean shutdown. I have attached the error as a jpg. 

I have reformatted this drive completely on windows, and it still comes up with this... Anyone know how I can fix this as it is pretty useless to me at the moment.. 

Thanks

Patrick

---

### Post by mouseboyx on 2007-12-02
Have you tried formating it as Fat32?

---

### Post by ozPATT on 2007-12-02
nope, can i do that using ubuntu? if so, how?

---

### Post by mouseboyx on 2007-12-02
install gparted
```

sudo apt-get install gparted

```
run it and select your hp drive from the right drop down menu its pretty straightforward after that

---

### Post by st33med on 2007-12-02
You also will have to do:
```
sudo gparted
```
after it installs. Otherwise, it will not start and say it is a 'weapon of mass destruction'. No, really :).

---

### Post by ozPATT on 2007-12-02
ok thanks, will give that a go

worked a treat thanks :D wow to think i was sitting on this for so long, and it only took a few mins to fix. :D thanks for the help. 

Patrick

---

