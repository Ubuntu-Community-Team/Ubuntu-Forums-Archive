---
title: "I'm Trying to install Xmms but i got this instead."
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by Solidad on 2006-05-27
i followed the instructions on the install. file and got this.

[IMG]http://i21.photobucket.com/albums/b289/Solidad2x/compilerproblem.png[/IMG]

what should i do?

---

### Post by Zdravko on 2006-05-27
Try
> 
sudo apt-get install build-essential


---

### Post by rejser on 2006-05-27
Or if it is ok with the one from the repos
sudo apt-get install xmms

---

### Post by Solidad on 2006-05-28
i got another error here.

[IMG]http://i21.photobucket.com/albums/b289/Solidad2x/error.png[/IMG]

what should i do?

---

### Post by user1397 on 2006-05-28
why don't you just install it using 
```
sudo aptitude install xmms
```

---

### Post by Grey on 2006-05-28
If you just want to use xmms, then the one from the repositories works perfectly fine.  It can be installed like this:

```
sudo apt-get install xmms
```

But if you are hell bent on compiling from source, then try this:

```
sudo apt-get build-dep xmms
```

Which will install all the dependencies needed for xmms.

---

### Post by Solidad on 2006-05-29
i dont have a internet connection, on ubunto so the repositiories wont work.

---

### Post by nalmeth on 2006-05-29
Can you get a .deb package over to the ubuntu PC somehow? then you can install it with 

sudo dkpg -i xmms.deb

For the last error, it told you that a described version of glib is required.

---

### Post by Perfect Storm on 2006-05-29
Then you might search for the package here [http://packages.ubuntu.com/](http://packages.ubuntu.com/) download it and burn/save it and thereafter put it on your ubuntu OS. Just make sure that you also get/have the dependency solved.
Next
```

cd /where/the/package/is
sudo dpkg -i XXXXXXXX.deb
```

---

### Post by Solidad on 2006-05-29
how do i get glib? is it pre build in the sympatic? or its on the net?

---

