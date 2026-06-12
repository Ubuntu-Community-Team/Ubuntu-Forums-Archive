---
title: "Anyone know how to use mirror sites as repositories?"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Koech on 2006-05-21
I have seen a mirror site nearer to my country rhan what I have been using(US, UK and Australia) the one in particular is in Namibia. I was wondering... how do I edit my [FONT="Courier New"]sources.list[/FONT] to download stuff from there? I rarely get speeds over 30kB/s with the others yet I can download better when doing other things.

---

### Post by oscar on 2006-05-21
If the mirror you are refering to is from this page: [http://www.ubuntu.com/download](http://www.ubuntu.com/download) then I think what you are refering to is a mirror for downloading the installation/live cds, I don't think it is a mirror for the repositories. You have to find a repository site, not a mirror.

---

### Post by DSn0wMan on 2006-05-21
[QUOTE=Koech]I have seen a mirror site nearer to my country rhan what I have been using(US, UK and Australia) the one in particular is in Namibia. I was wondering... how do I edit my [FONT="Courier New"]sources.list[/FONT] to download stuff from there? I rarely get speeds over 30kB/s with the others yet I can download better when doing other things.[/QUOTE]

To edit your sources.list just do this
```
sudo vi /etc/apt/sources.list
```

---

### Post by henriquemaia on 2006-05-21
[quote=DSn0wMan]To edit your sources.list just do this
```
sudo vi /etc/apt/sources.list
```[/quote] 
Just a small note: **absolute beginner talk** and **vi**???

gedit suits best or even nano for the cli.

```
 sudo gedit /etc/apt/sources.list
```

ps: don't mean to offend.

---

### Post by Koech on 2006-05-21
I'm sorry I didn't explain clearly. I know how to edit the sources.list, but only to the extent of changing the prefix: us. or au. or uk. but the sites I have in mind are not officially so. Look at this: [ftp://ftp.sun.ac.za/ftp/ubuntu/](ftp://ftp.sun.ac.za/ftp/ubuntu/). It's a nearby mirror site with not only install and live isos but also packages. How do I make them accessible to synaptics?

---

### Post by DSn0wMan on 2006-05-21
[QUOTE=henriquemaia]Just a small note: **absolute beginner talk** and **vi**???

gedit suits best or even nano for the cli.

```
 sudo gedit /etc/apt/sources.list
```[/QUOTE]


You are probably right. I just find vi alot easier to use, after trying it a couple of times.

---

### Post by DSn0wMan on 2006-05-21
[QUOTE=Koech]I'm sorry I didn't explain clearly. I know how to edit the sources.list, but only to the extent of changing the prefix: us. or au. or uk. but the sites I have in mind are not officially so. Look at this: [ftp://ftp.sun.ac.za/ftp/ubuntu/](ftp://ftp.sun.ac.za/ftp/ubuntu/). It's a nearby mirror site with not only install and live isos but also packages. How do I make them accessible to synaptics?[/QUOTE]

I am not sure about using ftp in sources.list

---

### Post by oscar on 2006-05-21
First you should back up your old sources.list just in case:
```
cp /etc/apt/sources.list ~/
```
Then you will want to edit your sources.list:
```
gksudo gedit /etc/apt/sources.list
```
and look for all of the lines that contain (ignoring the prefix):
```
http://uk.archive.ubuntu.com/ubuntu/
```
and replace that part with:
```
ftp://ftp.sun.ac.za/ftp/ubuntu/
```
Save the file and test if it works:
```
sudo apt-get update
```
I tested it (not with all of the lines, just one) and it seems to work

---

### Post by Koech on 2006-05-21
Thanks alot, I'll try it.

---

