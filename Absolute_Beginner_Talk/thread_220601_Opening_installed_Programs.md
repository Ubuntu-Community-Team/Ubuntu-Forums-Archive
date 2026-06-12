---
title: "Opening installed Programs"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by mattfender on 2006-07-21
I have had this problem with two programs, Frostwire most recently. Downloaded and installed it and it shows up under Applications>Internet.....but when I click it the program won't open. I tried the Applications>Add/Remove but it doesn't show up there either.

What do I do?

---

### Post by A2A on 2006-07-21
Have you tried reinstalling it?

---

### Post by Jagot on 2006-07-21
Have you installed Sun's Java first?  Can cause problems if you haven't.

---

### Post by lamego on 2006-07-21
When a program doesn't start from the menu you should open a terminal and try to run it writing the program name.
Running from a terminal will usually give you some error message.

---

### Post by patrick295767 on 2006-07-21
> **mattfender said:**
> I have had this problem with two programs, Frostwire most recently. Downloaded and installed it and it shows up under Applications>Internet.....but when I click it the program won't open. I tried the Applications>Add/Remove but it doesn't show up there either.

What do I do?

//to check if installed:
```
dpkg -l | grep myprogram
```
  
// First,```
 apt-get -f -y install mc
```
To check what is installed from apt-get -f :
go with mc program in the folder /var/cache/apt/archives
you'll find deb's files, enter into them and look what's installed. 
  
Same for any debs.

// taht's some ways ... other can be used ... 
...

gr(eetz

---

### Post by mattfender on 2006-07-21
I have tried re-installing it but that doesnt' work. I think I have Java but I am not sure.
what's the code to get the most recent update?

---

### Post by Jagot on 2006-07-22
> **mattfender said:**
> I think I have Java but I am not sure.
what's the code to get the most recent update?

Enable the multiverse repo, then:

```
sudo aptitude update && sudo aptitude install sun-java5-bin
```

You'll then need to run the following command to selece Sun's Javav:

```
sudo update-alternatives --config java
```

---

