---
title: "Dictionary needed"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-01-31
Dear friends, the default dictionary provided by ubuntu doesn't suffice for me. I like oxford online dictionary to be added. It is askoxford.com. But I can't add this one to the dictionary list. Kindly instruct me how to do it. What is the port of this dictionary? The address is [http://www.askoxford.com]("http://www.askoxford.com")
Thanks and regards,
Saurav

---

### Post by sauravbhaumik on 2007-02-01
Isn't there anyone to help me?

---

### Post by bobpur on 2007-02-01
If you open up your browser and right click on the little "Google" icon you can add more search engines. You also, have a couple of dictionary choices there, too.
I'm not in front of my Ubuntu machine right now, but I seem to remember finding this while "exploring" one day.
I don't know if this helps, it's just another choice you have.

---

### Post by ComplexNumber on 2007-02-01
i recommend that you install a program called stardict(you will find it in the repositories when you fire up synaptic). then downloadl the advanced oxford learners  dictionary [here]("http://stardict.sourceforge.net/Dictionaries_dictd-www.dict.org.php"). then move the files to /usr/share/stardict/dic. you can also add your own online dictioneries such as askoxford.

the port is 2628

---

### Post by sauravbhaumik on 2007-02-01
> **ComplexNumber said:**
> i recommend that you install a program called stardict(you will find it in the repositories when you fire up synaptic). then downloadl the advanced oxford learners  dictionary [here]("http://stardict.sourceforge.net/Dictionaries_dictd-www.dict.org.php"). then move the files to /usr/share/stardict/dic. you can also add your own online dictioneries such as askoxford.

the port is 2628

Thanks, but the directory /usr/share/stardict/dic  needs some permission so that I may copy and paste the downloaded dictionary file there. So, I can't move the downloaded dictionary rpm file to the specified directory. may be sudo su command is needed to log in as root; but I am not sure how to log in as root and be permitted to paste the file in that directory. Kindly help me.

---

### Post by ComplexNumber on 2007-02-01
> **sauravbhaumik said:**
> Thanks, but the directory /usr/share/stardict/dic  needs some permission so that I may copy and paste the downloaded dictionary file there. So, I can't move the downloaded dictionary rpm file to the specified directory. may be sudo su command is needed to log in as root; but I am not sure how to log in as root and be permitted to paste the file in that directory. Kindly help me.
all you have to do is use sudo and type in **your own** password. download the tarball, right click on it, select 'extract here'. then fire up the terminal and go into the extracted contents, then type:
[B]sudo cp * /usr/share/stardict/dic


[/B]don't get the rpm file because it won't work on ubuntu - get the other one[B].
[/B]

---

### Post by sauravbhaumik on 2007-02-02
> **ComplexNumber said:**
> all you have to do is use sudo and type in **your own** password. download the tarball, right click on it, select 'extract here'. then fire up the terminal and go into the extracted contents, then type:
[B]sudo cp * /usr/share/stardict/dic


[/B]don't get the rpm file because it won't work on ubuntu - get the other one[B].
[/B]

Thanks a lot; I have done it. Can you tell me wherefrom the concise oxford dictionary (COD) can be downloaded? I mean, as you have referred to the sourcefourge site where plenty of dictionary files are there, can you favour me by referring to something alike where I can get COD?

---

### Post by ComplexNumber on 2007-02-03
> **sauravbhaumik said:**
> Thanks a lot; I have done it. Can you tell me wherefrom the concise oxford dictionary (COD) can be downloaded? I mean, as you have referred to the sourcefourge site where plenty of dictionary files are there, can you favour me by referring to something alike where I can get COD?
i have no idea. unless anyone else knows, your best bet is trying google.

---

### Post by nike984 on 2007-02-03
> **sauravbhaumik said:**
> Thanks, but the directory /usr/share/stardict/dic  needs some permission so that I may copy and paste the downloaded dictionary file there. So, I can't move the downloaded dictionary rpm file to the specified directory. may be sudo su command is needed to log in as root; but I am not sure how to log in as root and be permitted to paste the file in that directory. Kindly help me.

You can also use GUI version.
```
gksudo nautilus
```

Then nautilus with root permission will popup.

---

### Post by clothrh on 2007-02-06
I simply extracted to /usr/share/stardict/dic from sudo nautilus and skipped the copy step.

---

