---
title: "Installing Many Fonts from a CDR"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by MetalPrincess on 2008-02-08
I have searched and cannot find any info on installing fonts outside the hard drive in the system. I have about 1000 fonts I want to install from a CDR disc. They are not zipped or compressed just in regular font format. I need a step by step on installing them. Please do not skin steps and assume I know what you are talking about because I do not. :( I'm new to linux stuff. Thanks

---

### Post by jan quark on 2008-02-08
try this

[http://laiconic.quotaless.com/gimp8.html](http://laiconic.quotaless.com/gimp8.html)

---

### Post by MetalPrincess on 2008-02-08
OK thanks for the response. However like I said I'm new so how do I Navigate to the font file in the terminal? What is the code when the font file is on the desktop?

---

### Post by jan quark on 2008-02-08
you navigate using the command cd

so for instace you want to get the file apple in the folder banana
you type into the terminal

```
cd /banana/apple
```


you can also do the following

type cd into the the terminal and then drag and drop the font file into the terminal after the cd and delete the     ' '   signs

---

### Post by jan quark on 2008-02-08
you can also look at the pic in my tutorial it is very step by step

---

### Post by MetalPrincess on 2008-02-08
ah ok did not think about the cd thing. Guess I need to think in terms of old DOS for some things LOL Thanks for the help :D

---

### Post by jan quark on 2008-02-08
no problem 

once you get used to the terminal things will dance in linux

and feel free to ask everything you want to know
we are here to help

---

### Post by MetalPrincess on 2008-02-08
Is there any possible way to add more than one at a time?

---

### Post by hyper_ch on 2008-02-08
you could also install midnight commander. Then you have a two-pane file manager in the terminal.

```

sudo apt-get install mc

```
and run it
```

mc

```

Copying is done with F5

---

### Post by hyper_ch on 2008-02-08
> **MetalPrincess said:**
> Is there any possible way to add more than one at a time?

```

cp /path/to/cd-drive/* /path/to/new/location/

```

---

### Post by jan quark on 2008-02-08
you can also browse through me new (created today) Beginner Command Tutorial 

see signature

---

### Post by MetalPrincess on 2008-02-08
Awesome! Thanks I got them all installed :D

---

### Post by metalguy639 on 2008-04-13
> **hyper_ch said:**
> ```

cp /path/to/cd-drive/* /path/to/new/location/

```

That is not working for me. I get an error message saying I do not have permission. I tried coping via the terminal & MC. Anyone know how to give myself permission for this?

---

### Post by hyper_ch on 2008-04-13
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

