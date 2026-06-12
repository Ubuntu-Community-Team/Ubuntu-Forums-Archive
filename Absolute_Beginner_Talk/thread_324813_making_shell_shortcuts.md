---
title: "making shell shortcuts?"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by westie on 2006-12-24
Hi Guys,
I want to set up a script or procedure so that i can type a word in the shell and it launches a program (like typing ffirefox or gaim for instance).  Everytime I want to run a program called houdini I have to type:

cd /opt/hfs8.1.666/
source houdini_setup_bash
houdini

and I really just want to type houdini without the other bits, I hear you can edit the .cshrc file, or u should make a new file and link to it, but I have absolutly no idea how to do either.

As usual talk to me like a complete newbie.

AnDy

---

### Post by MkfIbK7a on 2006-12-24
you can use the run line from the panel menu 
Example: **MENU** > **RUN** > type **"HOUDINI"**
this should work unless the bin file is named something else

---

### Post by konst88 on 2006-12-24
There is a file in your home directory called: .bashrc
open it with gedit and add the following to the end of it:
```
function houdini {
    cd /opt/hfs8.1.666/
    source houdini_setup_bash
    houdini
}
```
Now you can just type houdini.
Hope it will work.

---

### Post by wildkarde on 2006-12-24
First, open the console and type the following.

cd
mkdir bin
echo PATH=$PATH:$HOME/bin >> .bashrc
cd bin
gedit houdini

Once the text editor opens, type this in.

cd /opt/hfs8.1.666/
source houdini_setup_bash
houdini

Save the file and exit.

Then type this back on the console, which should still be open.

chmod +x houdini

And that's it.  It should now work whenever you run it from the console.

---

