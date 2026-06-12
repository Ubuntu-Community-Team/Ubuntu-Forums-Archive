---
title: "How can I remove the Ubuntu CD from the Repos of Synaptic with Terminal Command"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-26
Hello Everybody !!!

I have a tough one here:

I want to type a command on the "Terminal" that does the following:

Removes the "Ubuntu CD" from the Repositories of "Synaptic Package Manager"


It must be stored somewhere deep (in some Ubuntu's file), so how can I change this?


You know, instead of:

1. launching "Synaptic Package Manager"

2. From the Menu, select "Settings\Repositories".

3. Select the first line in the list, named "CD Ubuntu 5.10 - Breezy Badger" & click 
    on the button named "Remove".

4. Click on the button named "OK" & then on the button named "Yes".

5. From the Menu, select "File" & "Quit", to close the "Synaptic Package Manager"


What can I type on the Terminal to perform the above?


Thanks.

---

### Post by bluevoodoo1 on 2006-02-26
if you want to do it completely in the terminal...

```
sudo nano /etc/apt/sources.list
```

then place a # in front of the ubuntu cd line

or you could use...

```
sudo gedit /etc/apt/sources.list
```

---

