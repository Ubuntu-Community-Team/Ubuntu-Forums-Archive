---
title: "Trying to Write an Easy Shell Script to Install a Program"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by dcdman67 on 2008-03-31
I am a total noob when it comes to scripting and Linux. I wanted to wrire a shell script to install Pysol. I know that you can get this program using sudo apt-get install pysol. How would I go about creatinga shell script to do this for me. I want to test my management software's distribution capabilities.....

Also, would I have to write something in the script to prompt for a password?

Thank you in advance.....:guitar:

---

### Post by kevin11951 on 2008-03-31
> **dcdman67 said:**
> I am a total noob when it comes to scripting and Linux. I wanted to wrire a shell script to install Pysol. I know that you can get this program using sudo apt-get install pysol. How would I go about creatinga shell script to do this for me. I want to test my management software's distribution capabilities.....

Also, would I have to write something in the script to prompt for a password?

Thank you in advance.....:guitar:

create a .sh file and in it write:

```
gksudo apt-get update && apt-get install pysol
```

if its in the repos, thats what you want.

---

### Post by kevin11951 on 2008-03-31
> **kevin11951 said:**
> create a .sh file and in it write:

```
gksudo apt-get update && apt-get install pysol
```

if its in the repos, thats what you want.

sry got it wrong, you want:

```
gksudo apt-get update && sudo  apt-get -y install pysol
```

---

### Post by dcdman67 on 2008-03-31
Thanks...I am going to try this out tonight....

---

### Post by Helios38 on 2008-03-31
wont sudo ask you for a password?


since its a shel script you wouldnt reli be getting any feedback until the script completes


am i right?...

---

### Post by dcdman67 on 2008-04-01
What ahould the commands be for unpacking and installing this shell script called pysol.sh

I figures that it would look something like this:

tere -xvzf /path to tar.gz/pysol.tar.gz | install /path to pysol.sh/pysol

Can anyone help here?

Thanks in advance....

Linux Noob

---

