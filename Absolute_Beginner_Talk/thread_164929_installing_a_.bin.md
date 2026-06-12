---
title: "installing a .bin?"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Snare on 2006-04-23
Im trying to install java but when i download it it gives it to me as a .bin...

what do i do?

---

### Post by krusbjorn on 2006-04-23
Type "./filename" in a terminal, after CD:ing to the directory you saved it in. I think you can double click it in nautilus and select "Run" too.

---

### Post by Ensnared on 2006-04-23
If you're installing the JRE from sun, then it's better to use the one in the repositories - you may have to enable the universe or multiverse repos in /etc/apt/sources.list if you haven't already. Then to install Java, do this:```
sudo apt-get install sun-j2re1.5
```
Then to make sure it will be used as the default Java engine, do this:
```
sudo update-alternatives --config java
```...and enter the number that refers to "/usr/lib/j2re1.5-sun/bin/java".

Anyway, usually when you download a .bin as an installation-file, it's simply a matter of executing it. If the file is named myprogram.bin you can do this by either```
chmod +x myprogram.bin
./myprogram.bin
```or```
sh ./myprogram.bin
```The first of the two will make the file executable (if it isn't already - I find that they aren't more often than not), and then run it. The other will run a shell which in turn will load the file and run it. The result is the same.

But I suggest you use apt to install Sun Java regardless - it's a lot cleaner that way :)

---

### Post by uzi09 on 2006-04-23
a really good website is:

[www.ubuntuguide.org](www.ubuntuguide.org)

it's the unofficial ubuntu starter guide. tells u step by step how to install a lot of these programs (including java).

basically, for binary (*.bin files) u can just run it using ./<binary>.
Ex: if ur file is calld java.bin, then
./java.bin

u may also have to make sure that its permissions allow executing.
you can check this by typing ```
 ls -l 
``` and check if there are x's in the permissions. if not, you can change it so by typing:
```
 chmod a+x java.bin
```

good luck, and let us know if u need any more help
uzi

---

### Post by Snare on 2006-04-23
ah thanks uzi!

```

chmod a+x java.bin

```

worked for me!

---

### Post by Snare on 2006-04-23
ok i got another question. i was reading that link posted, and it says to try

```

sudo apt-get install flashplayer-mozilla

```

but it says it cant find the package.

and is there a list somewhere of all these packages or what? somewhere i can search for them?

---

### Post by Qrk on 2006-04-23
Try this instead:

```
sudo apt-get install flashplugin-nonfree
```


> and is there a list somewhere of all these packages or what? somewhere i can search for them?

For the non-free media packages, follow this guide:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Or look under System->Help-> Starter guide.

---

### Post by unbuntu on 2006-04-23
[QUOTE=uzi09]a really good website is:

[www.ubuntuguide.org](www.ubuntuguide.org)

it's the unofficial ubuntu starter guide. tells u step by step how to install a lot of these programs (including java).
[/QUOTE]

FYI, this guide is for 5.04, which is a bit outdated.  You may want to check out the guide for Breezy
```

http://easylinux.info/wiki/Ubuntu

```

---

### Post by Snare on 2006-04-23
ok i got it to install and did the update thing and it gave me the folder

```

/usr/lib/jvm/java-gcj/bin/java

```

which i specified for it to use as java

but when i go  into firefox it still acts as tho i havn't installed it and says im missing plugins...

thanks for the help so far!

---

### Post by Qrk on 2006-04-23
You need to make a symbolic link from your plugins folder, which is /usr/lib/mozilla-firefox/plugins and the libjavaplugin.so file in your java directory.

```
cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /path/to/java/plugin/libjavaplugin.so 
```

---

### Post by Snare on 2006-04-23
ok i will try that

one more question.

is the only difference in kubuntu and ubuntu the graphical interface they use? because i saw a screenshot of kubuntu and i really like it.

---

### Post by Qrk on 2006-04-23
Yes. Kubuntu uses KDE and ubuntu uses Gnome. In fact you can have both desktop environments installed at the same time. 
You can try it out.

```
sudo aptitude install kubuntu-dekstop
```

You can choose whether to run Gnome or KDE at the login screen.

---

### Post by Nikusan on 2006-04-23
[QUOTE=Snare]Im trying to install java but when i download it it gives it to me as a .bin...

what do i do?[/QUOTE]

Your best bet is to follow the instructions [here.]("https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca")

If you follow these instructions you will be able to manage your java install just like all the other software on your system using apt / synaptic. The .deb that is created will also handle the firefox plugin as well as some other benefits.

Once it is installed do a
```
sudo update-alternatives --config java
```
to choose the new sun java.

---

