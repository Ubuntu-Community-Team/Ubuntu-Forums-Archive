---
title: "installing packages"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by rikguenther on 2006-11-23
how in the world do i install things?  i download them as a tar.gz or whatever, uncompress it, and am left staring blankly at my screen because i dont know what to do... any help?

---

### Post by NetworkGuy on 2006-11-23
Well, what are you trying to install?   Chances are, Ubuntu has a package that will automatically install it.

---

### Post by rikguenther on 2006-11-23
im trying to install a game called 'sauerbraten' i guess its a FPS or whatever. but yea any suggestions?

---

### Post by rfruth on 2006-11-23
Use the package manager !

---

### Post by rikguenther on 2006-11-23
ive tried synaptic but it yeilded no results, so is there a way to install a package locally like from my machine?  like is there a way i can use synaptic to install a file i downloaded, not one from the repositories?

---

### Post by NetworkGuy on 2006-11-23
That one isn't there by default.  When you uncompressed the tar file you should see a file that should talk you through the installation.  Look for that first.

---

### Post by rikguenther on 2006-11-23
there is a readme file that tells me to go into the terminal and "chmod" a certain file in the folder.. but i dont know what that means and when i do it it doesnt do anything

---

### Post by CatKiller on 2006-11-24
[This page]("http://monkeyblog.org/ubuntu/installing/") will guide you through the basics of what you're trying to do. As too will [this one]("http://www.psychocats.net/ubuntu/installingsoftware").

chmod changes the access permissions of a file. You needed to do that to make the file executable (+x). That probably wasn't **all** that the readme told you to do, is it?

---

### Post by rikguenther on 2006-11-24
> For GNU/Linux: gunzip, chmod +x sauerbraten_unix and then ./sauerbraten_unix. Needs a decent and compliant OpenGL implementation.

that is what the readme is telling me to do to install it.  im not quite sure what to do here.

---

### Post by Voxxi on 2006-11-24
Ok, basically what it is asking you to do is:

1. Decompress (Unzip the file)
2. Make it so that you can run the file
3. Run the file

So lets do it!

**Decompressing the file**
1. To unzip the file, just find the .tar.gz file and double click it. It should open in something called "Archive Manager". Its a bit like Winzip. 
2. Press extract up the top, and in the dialog select the option that says "All files".
3. Click on the "Extract in" list and click "Other".
4. Make sure you are in your home folder, it should be named the same as your username. If you aren't or aren't sure, double click your username in the left pane.
5. Click "Create folder" and name it something like "game", remember to have it all lowercase, and hit enter.
6. Click "Open" and then "Extract".

**Making the file "runnable"**
1. Open up a terminal (Applications -> Accessories -> Terminal)
2. Now type:
```
cd game
```

If you didn't name it game, replace "game" with whatever you named it.

3. Type :
```
sudo chmod +x sauerbraten_unix
```

4. Enter your login password

In Linux, chmod changes the "permissions" for a file. Permissions dictate who can read, write to or execute a particular file. This is a security measure. chmod +x changes the file permissions so it can be executed. 

You might have noticed a "sudo" in there. What sudo does is runs the command you type after it as "root". Root is a user account, similar to what "Administrator" is in Windows. Root can do anything, access other peoples file, delete or modify important file etc. Be careful when you're root, as if you type in a command without knowing what you're doing you 
can wreck your system.

**Running the file**

In your terminal type:
```
./sauerbraten_unix
```

What that does is similar to double clicking an .exe in Windows. Its runs the file name "sauerbraten_unix".

Thats it! Your game should run now. ;) Let me know if there are any more problems.

---

