---
title: "Help with RAR files please"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Ciwan on 2007-12-01
Hi guys

I'm new to Ubuntu so please go easy on me.

How do I extract [.rar] files in Ubuntu ?

A clear step by step method would be much appreciated, as I don't know a single thing about Ubuntu.

Thanks

---

### Post by alienexplorers on 2007-12-01
I believe unrar is what your looking for.  It can be found in the repositories.

---

### Post by adityakavoor on 2007-12-01
```
sudo apt-get install rar
```

---

### Post by illbashu on 2007-12-01
> **adityakavoor said:**
> ```
sudo apt-get install rar
```

its...
```
sudo apt-get install unrar
```

---

### Post by sethvath on 2007-12-01
sudo apt-get install rar unrar  

After you installed rar, right click on the rar file and choose extract here

---

### Post by Ciwan on 2007-12-01
Guys What do I do with that code ???

I don't know a thing about Ubuntu !! :(

Am I suppose to paste that code in my internet browser ??

---

### Post by prab97 on 2007-12-01
p7zip too can unrar files.

---

### Post by SunnyRabbiera on 2007-12-01
Yeh unrar is what you need, unrar will allow ubuntu to extract the files you desire.
here is how to install it:
go to system in the main menu, then to "administration"
click on "synaptic package manager"
now unrar is in the multiverse repositories, to enable it go to "settings" in the synaptic menu and click on "repositories"
after that a window saying "software sources" will pop up
now click on the boxes without a checkmark to make sure the repositories are loaded
now click "close"
now synaptic will probably tell you to restart it, just click "close" and click the button that says "reload"
once it reloads search for "unrar"
after that you should see unrar in your list, just click on the box next to it and select "mark for installation"
now if it needs extra packages, its fine just click the "mark" button
after that click on the "apply" button in the next window that will pop up
let it load and install your files
after that just close the installation window and then synaptic
and you are done :D

---

### Post by prab97 on 2007-12-01
1. In the System menu click Administration. There click Synaptic Package Manager.
2. Click Reload in the toolbar. For this to work, you must have your internet connected.
3. After the Reload thing completes, click search in the toolbar, There type "unrar" or "p7zip" without quotes.
4. After the results are displayed, select the app you wanna install. Then click Apply.
5. Synaptic will automatically download and install the app.

After that use command line option to extract ur rar file.

---

### Post by Lord DarkPat on 2007-12-01
Use [PeaZip](www.peazip.org)
I find it better than Ark. Plus, it's as amall as pea :lolflag:

---

### Post by Ciwan on 2007-12-01
Cool Thanks for your help guys

I have [unrar] installed now. When I go to that place again It has a green box next to it, which means it is installed right ? :)

---

### Post by JonathanRRogers on 2007-12-01
The standard GUI archive utility file-roller can extract from RAR files. However, it requires that the an "unrar" command be installed. As previously mentioned, you can type "sudo apt-get install unrar" into a terminal window.

If you prefer to use a GUI, you can start the Synaptic Package Manager from the System->Administration menu at the top of the screen. In Synaptic, select Settings->Repositories, and make sure the check box labeled "Software restricted by copyright or legal issues (multiverse)" is checked. Close the dialog box and click the Reload button. Then, use the Search button to find packages with "unrar" in the name. Double-click on the package called simply "unrar" then click Apply and Apply again in the dialog box. A new dialog will open and indicate when the package has been installed.

When you have installed the unrar package, you can open a RAR archive by double-clicking it in the file manager (nautilus).

Note that the official rar and unrar commands are proprietary software and most of these steps are not needed to work with freer archive formats like tar and zip.

---

### Post by sethvath on 2007-12-01
Yes, and you might wish to spend some time on [https://help.ubuntu.com/](https://help.ubuntu.com/) and [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy) to get yourself familiar with ubuntu. The command line is not that scary

---

### Post by Ciwan on 2007-12-01
Cool thanks a lot Bro,

All your help has been much appreciated :)

Thanks :)

---

### Post by adityakavoor on 2007-12-05
> **illbashu said:**
> its...
```
sudo apt-get install unrar
```

sudo apt-get install rar    works like a charm

---

