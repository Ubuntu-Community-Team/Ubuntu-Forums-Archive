---
title: "How can I add  Houdini to my Applcations Graphics menu"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by dabsan on 2007-09-09
I recently installed Houdini 9 beta, I can launch the program from the Terminal with the follow commands :

cd /opt/hfs9.0.702
source houdini_setup_bash
houdini

But I would like to launch the program from the Applications Graphics menu. Can anybody tell me how to do that ... hope somebody can explain the way to do this.
Many Thanks

---

### Post by mocoloco on 2007-09-09
I played around with Houdini a bit last year.  I should re-install and get back in to that, when I have some time... :)

Probably what you want to to is first make it do the source step for you.  On [this page]("http://www.sidefx.com/index.php?option=com_content&task=view&id=683&Itemid=229"), at the bottom after step 5 it tells you how to make it start automatically for each shell.
Then you just need to right-click on the Applications menu, do "Edit Menus" and you can add a new entry under Graphics.  Try it as type Application first, and if that doesn't work you may have to change it to type "Application in Terminal".  The command will just be "houdini", and there's probably an icon somewhere in /opt/houdini<version> that you can use.
I will probably install it later today or tomorrow, and I'll re-post if I was wrong about any of that.

---

### Post by dabsan on 2007-09-10
Mocoloco,thanks for your reply. I followed the steps on the webpage link you sent me but I don`t understand how to do the this last part :-

[U]You will need to source houdini_setup in each shell that you run Houdini. You can add the following code to your .login file to automatically do this:

pushd /opt/hfs8.2.13 <- use the build version that has been installed
source houdini_setup bash
popd[/U]

Can you please try to help me ... what is the .login file ? Where do I put the code?

Did you install your houdini again?  
Many thanks

---

### Post by mocoloco on 2007-09-15
Sorry I didn't get back to your sooner, life sometimes gets in the way :).  You may have already figured this out, but if not here's what I did to add it to my menu.

I couldn't get the instructions on their site to work, creating a .login file and adding that data.  Instead of worrying about that I decided to just have a shell script launch it.  This has the added benefit that if other users want to run Houdini they don't have to set anything up.  My Houdini is in /opt/hfs9.0.702 but obviously you'll need to put the correct path if yours is different.  Open a terminal, and type
```
sudo gedit /opt/hfs9.0.702/houdini.sh
```
That will creat the shell script file, then copy and past this text into it
```
#!/bin/bash
cd /opt/hfs9.0.702
source houdini_setup_bash
houdini
```
Close Gedit, saving the file.  Now we make it executable
```
sudo chmod 755 /opt/hfs9.0.702/houdini.sh
```

I was surprised that nowhere included was an icon or image of the logo for a launcher icon.  I ended up installing the windows version on another machine, and that didn't have a standalone icon file either, so I ended up finding an extraction program and creating an ico file.  I've attached it to this post.
Download that, right-click it and extract it.  then back in your terminal cd to the directory the icon's in and do
```
sudo mv houdini.ico /opt/hfs9.0.702
```

Finally, adding it to your menu.  As I mentioned in the previous post you could right click your menu and add it there, however that only adds it for your user, not all users.  Unfortunately Alacarte (the menu editing tool) doesn't do items for all users, but we can easily do that ourselves. 
```
sudo gedit /usr/share/applications/houdini.desktop
```
Paste this in.  Remember to change the path if yours is different.
```
[Desktop Entry]
Encoding=UTF-8
Name=Houdini Master 9
Comment=Procedural 3D animation and special effects tool
Exec=/opt/hfs9.0.702/houdini.sh
Icon=/opt/hfs9.0.702/houdini.ico
Terminal=false
X-MultipleArgs=false
Type=Application
Categories=Graphics;3DGraphics;
```

Now you should see Houdini Master 9 under Applications -> Graphics.  Have fun :).

---

### Post by dabsan on 2007-09-17
Hi, thank you very much for getting back to me......... 
Yes I now have it listed in my Applications, Graphics menu. And everything is working ok.
Many thanks for all your help.
:D :D :D

By the way I couldn`t see the icon attached to your posting so I grab one myself.
I will post it up here in case anyone else needs it.

---

### Post by mocoloco on 2007-09-17
Guess I forgot to attach my file :oops:.  Glad to see you got everything set up.

---

### Post by framebuffer on 2007-10-15
I followed the procedure exactly, but when I try to run houdini it gives the following error:

The Houdini 9.0.747 environment has been initialized.
/opt/hfs9.0.747/bin/hkey-bin: error while loading shared libraries: libpython2.5.so.1.0: cannot open shared object file: No such file or directory

I tried hunting for libpython2.5.so.1.0 and putting it in the folder /opt/hfs9.0.747/bin/hkey-bin but then I get a segmentation fault.

Any ideas?

---

