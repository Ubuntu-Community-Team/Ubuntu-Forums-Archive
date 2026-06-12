---
title: "Adminstrator password help"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Dionysus135 on 2007-08-18
Im using xubuntu 7.04 and im still kind of new at xubuntu.But when I go on Applications--->System--->Time/Date it ask for the admin password.I tried putting in my regular user password but nothing happens and when I click on Time/Date its denied.How do i adjust the Time/date?

---

### Post by taurus on 2007-08-18
Do you belong to groups adm & admin?  See if you are from the output of this command from a terminal.

```
id
```
What happens if you run this command from a terminal and use the same password that you use to log in?

```
sudo aptitude update
```

---

### Post by kwacka on 2007-08-18
How many user accounts do you have? 

You need to use the account/password you used when you installed.

make sure that you use the correct case i.e. TOM is not the same as Tom.

---

### Post by Dionysus135 on 2007-08-18
> **taurus said:**
> Do you belong to groups adm & admin?  See if you are from the output of this command from a terminal.

```
id
```
What happens if you run this command from a terminal and use the same password that you use to log in?

```
sudo aptitude update
```

Well when i typed in id the only thing that had adm was group=4 (adm)

When i typed in the sudo aptitude update i got all errors.I dont have internet connection at the moment right now.

---

### Post by taurus on 2007-08-18
Can you post the output of this command?

```
cat /etc/group
```

---

### Post by Dionysus135 on 2007-08-18
> **taurus said:**
> Can you post the output of this command?

```
cat /etc/group
```

I just typed in that command and a lot came up.Is there anything specifcally are you looking for?

---

### Post by taurus on 2007-08-18
Just want to see if there is a group admin (near the end of the file) and whether you belong to that group or not since looks like you are not right now.

---

### Post by Dionysus135 on 2007-08-18
I see admin: x:117: (My screename)

---

### Post by Dionysus135 on 2007-08-18
> **taurus said:**
> Just want to see if there is a group admin (near the end of the file) and whether you belong to that group or not since looks like you are not right now.

Yea i see admin but im not sure if i belong in a group.

---

### Post by taurus on 2007-08-18
If you just post the output of the command that I've asked for, then we will know for sure and I can tell you what to do next.  Otherwise, I am not going to play a guessing game since I have other things to do.

```
cat /etc/group
```

---

### Post by Dionysus135 on 2007-08-18
> **taurus said:**
> If you just post the output of the command that I've asked for, then we will know for sure and I can tell you what to do next.  Otherwise, I am not going to play a guessing game since I have other things to do.

```
cat /etc/group
```

Im sorry if im wasting your time but i cant really copy and paste im using xubuntu on a different cpu, but I have a screenshot near the bottom what you said you were looking for.

[http://img527.imageshack.us/img527/1320/049iz9.jpg](http://img527.imageshack.us/img527/1320/049iz9.jpg)

---

