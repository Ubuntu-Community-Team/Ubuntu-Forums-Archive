---
title: "How to extract .bin file"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-09-24
Hi Can someone please tell me i easy babysteps how to extract a bin file and put it where desired?

I am thinking in particular about java as a working example because that is what i'm having trouble installing despite the wiki, which is to my newbie capacity overwhelming with lots and lots of imcomprehension

jdk-1_5_0_05-linux-i586.bin

how do i extract this.bin file and install java?

thank you,

--
sophtpaw

---

### Post by Xian on 2005-09-24
[QUOTE=sophtpaw]jdk-1_5_0_05-linux-i586.bin

how do i extract this.bin file and install java?
[/QUOTE]
First, cd to the location of the file in a terminal.
Then you just need to make it executable & run it as admin.

```
$ cd /path_to_file
$ sudo chmod a+x jdk-1_5_0_05-linux-i586.bin
$ sudo ./jdk-1_5_0_05-linux-i586.bin
```

---

### Post by bored2k on 2005-09-24
You do not extract, you just install it with
```
sudo bash jdk-1_5_0_05-linux-i586.bin
``` 

I do not like this method, I simply do (I use JRE, not JDK btw):
```
sudo apt-get install fakeroot java-package
```
```
fakeroot make-jpkg jdk-1_5_0_05-linux-i586.bin
```
```
sudo dpkg -i *.deb
```

---

### Post by sophtpaw on 2005-09-24
[QUOTE=Xian]First, cd to the location of the file in a terminal.
Then you just need to make it executable & run it as admin.

```
$ cd /path_to_file
$ sudo chmod a+x jdk-1_5_0_05-linux-i586.bin
$ sudo ./jdk-1_5_0_05-linux-i586.bin
```[/QUOTE]

If my package was downloaded to /home/conrad/downloads'

do i need to send it somewhere else?
I don't understand cd /path_to_file ?

thx for expanding on that command

--
sophtpaw

---

### Post by PsyberOneZero on 2005-09-24
> do i need to send it somewhere else?
I don't understand cd /path_to_file ? 

It's just shorthand for the purpose of the forum, it means just cd to the path that you downloaded the file in your case
```
#cd /home/conrad/downloads
```

hope that clears it up

---

### Post by sophtpaw on 2005-09-24
[QUOTE=PsyberOneZero]It's just shorthand for the purpose of the forum, it means just cd to the path that you downloaded the file in your case
```
#cd /home/conrad/downloads
```

hope that clears it up[/QUOTE]


thank you for clarification


--
sophtpaw

---

