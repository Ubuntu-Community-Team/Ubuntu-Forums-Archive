---
title: "Newb problem- folder permissions"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Patch86 on 2007-02-09
Frustrating problem, the kind that I just know has a painfully obvious answer, if only I knew what it was.......

Was trying to install codecs for MPlayer. Went to put them in the /usr/local/lib/codecs or /usr/local/lib/win32 directory, but the neither folder existed. I tried to create the folder (in the extractor, using the file browser, and using the terminal), but no joy; I'm told "permission denied". Since the directory belongs to the root user, and I've been yelled at on-pain-of-death that logging in as root is desperately not necessary and just shouldn't be done if you can at all help it (which, "they" say, you always can).

So, what do I do?

---

### Post by RomeReactor on 2007-02-09
Open a terminal and navigate to the **/usr/local/lib**

```
cd /usr/local/lib
```

and issue the make directory command prepending **sudo**

```
sudo mkdir win32
```

and

```
sudo mkdir codecs
```

Any time you must issue commands that are to be run as root, use **sudo**. Just be careful; Linux won't ask you if you're sure you want to format your hard drive or erase your entire home folder.

---

### Post by Patch86 on 2007-02-09
Ah, see? Simple and obvious :P

Thanks matey!

---

### Post by Maestro23 on 2007-02-09
> **Patch86 said:**
> Ah, see? Simple and obvious :P

Thanks matey!

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Patch86 on 2007-02-09
Ok, while we're at it:

I now need to extract the codec (essential-20061022.tar.bz2) to the folder in question (/usr/local/lib/codecs), and it gives me the same permission refusal when trying to do it by the GUI.  So what would the terminal command be to extract that file to that directory?

---

### Post by RomeReactor on 2007-02-09
Now open the terminal, again navigate to the folder containing the .tar file, and

```
sudo cp essential-20061022.tar.bz2 /usr/local/lib/codecs
```

now go to the **codecs** folder in the terminal, and

```
sudo tar -xvf essential-20061022.tar.bz2
```

I think that should do it.

An easier way to do all this is to

```
sudo nautilus
```

make the folders, copy/paste the .tar file and extract it. I don't know why a lot of people are paranoid about opening applications as root; sure it poses the danger of doing harm to your system, but instead of making others equally paranoid, we should just make them aware of the risks and let them decide on their own whether to do use it or not. Issuing sporadic commands as root is really not that big of a deal; logging in as root and staying that way, however, makes no practical sense.

---

### Post by Maestro23 on 2007-02-09
> **RomeReactor said:**
> Now open the terminal, again navigate to the folder containing the .tar file, and

```
sudo cp essential-20061022.tar.bz2 /usr/local/lib/codecs
```

now go to the **codecs** folder in the terminal, and

```
sudo tar -xvf essential-20061022.tar.bz2
```

I think that should do it.

Good stuff from Rome.  [COLOR="Red"]/usr[/COLOR] is owned by [COLOR="Red"]root[/COLOR], that is why you need [COLOR="Red"]sudo[/COLOR].

Here's a good link for you to read in your downtime as well.  Get your feet wet: [http://www.linuxcommand.org/lts0040.php](http://www.linuxcommand.org/lts0040.php)

---

### Post by Patch86 on 2007-02-09
thats not working. Not sure what I'm doing wrong on this one. 

This is what I did:

> cd /home/patch/Downloads

Which is where the file is, confirmed in the GUI.

> sudo cp essential1022.tar.bz2 /usr/local/lib/codecs

And I get:

> cp: cannot stat `essential1022.tar.bz2': No such file or directory

---

### Post by Maestro23 on 2007-02-09
> **Patch86 said:**
> thats not working. Not sure what I'm doing wrong on this one. 

This is what I did:



Which is where the file is, confirmed in the GUI.



And I get:

You have to make the codecs dir first. Not there by default.

#cd /usr/local/lib
#sudo mkdir codecs

---

### Post by Patch86 on 2007-02-09
Yah, already done that.

---

### Post by Patch86 on 2007-02-09
Doh, my fault, simple typo. Probably a sign I should call it a night :P

---

### Post by chick penguin on 2007-02-09
> **Maestro23 said:**
> 

Here's a good link for you to read in your downtime as well.  Get your feet wet: [http://www.linuxcommand.org/lts0040.php](http://www.linuxcommand.org/lts0040.php)

Excellent link, thanks! Save, print.

---

