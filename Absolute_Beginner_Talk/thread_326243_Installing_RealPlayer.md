---
title: "Installing RealPlayer"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by lift_test on 2006-12-27
Please, step by step idiots guide to installing downloaded as opposed to package manager programs.  Have allready bent some things trying.

---

### Post by ron999 on 2006-12-27
Hi

If you're comfortable with using Automatix2, this will install RealPlayer for you, no sweat.
Here:- [http://www.getautomatix.com/]("http://www.getautomatix.com/")
:cool:

edit:- I've just seen pay's reply below. doh! :-) I forgot the obvious :-)

---

### Post by pay on 2006-12-27
```
sudo aptitude install realplay
```

---

### Post by Vorian on 2006-12-27
check this post
[http://www.ubuntuforums.org/showpost.php?p=1906616&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1906616&postcount=5)

---

### Post by Bloch on 2006-12-27
I wasted a lot of time with tar balls, make commands and the like before I realised that synaptic (= apt-get commands in the terminal) is the way to go. If it's not in the repositories, then it is specialist / beta software, or proprietary stuff.

This being the Absolute Beginner Talk, it's fair to warn beginners to expect difficulties and challenges when they try to install software by other means.

> Please, step by step idiots guide to installing downloaded as opposed to package manager programs. 
There isn't going to be an idiot's guide, because "idiots" (humorously meant) should stay with synaptic.

---

### Post by 56phil on 2006-12-27
Download the bin file from the web to a working directory.

Make it executable
```
chmod a+x Real*.bin
```
Run the bin file:
```
sudo ./Real*.bin
```
Answering the questions in the affirmative and take the default when asked about symbolic links.

Delete the bin file.
```
rm Real*.bin
```
That should do it. 

Good Luck.

---

### Post by Fastball on 2006-12-27
> **pay said:**
> ```
sudo aptitude install realplay
```

about the "aptitude".. does that code would search a package in the pc or in the internet??

---

### Post by ron999 on 2006-12-27
> **Fastball said:**
> about the "aptitude".. does that code would search a package in the pc or in the internet??

.... gets it from the repository... on your pc:)

---

### Post by lift_test on 2006-12-27
Thanks for all the replies, have installed and is working - eventually - problem was with the path (is that DOS or Linux terminology or both?) between cmod etc and Real*.

---

### Post by Fastball on 2006-12-27
> **pay said:**
> ```
sudo aptitude install realplay
```

about the "aptitude".. does that code would search a package in the pc or in the internet??

---

### Post by Vorian on 2006-12-27
> **Fastball said:**
> about the "aptitude".. does that code would search a package in the pc or in the internet??

aptitude = apt-get   

both get the software from the ubuntu or other repositories listed in your sources via the Internet:)

---

