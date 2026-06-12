---
title: "Alias connect to stream"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by ubz on 2007-06-23
Hi, I'd like to make an alias that will both launch mplayer from the shell and connect to a radio stream.  I know a little about setting up aliases in ~$ .bashrc and tried this.

alias cbc1t='mplayer mms://wm.cbc.ca/cbcr1-toronto'

This syntax doesn't work. Is there a way to include a url as part of the alias command? -thanks

---

### Post by alan_daniel on 2007-06-23
I'm not sure how to do that using an alias, but you could always set up a simple shell script to do it. If you've never used a script before, it's basically a small little file that you can run. You can put the command in that file, make it executable, and move it to /usr/local/bin/, which will allow you to just type in that command like you would any other program.

To do it that way, here's what you should do:

1. First decide whatever you want the command to be (whatever the alias would have been...looks like you wanted cbc1t)
2. Open a file with that name, no extensions, using vi or something similar.
3. In that file, all you need to type is this:
```
mplayer mms://wm.cbc.ca/cbcr1-toronto
```
4. Save the file and make it executable...if you don't know how to do that, here's the command:
```
sudo chmod +x cbc1t
```
5. Move the file to /usr/local/bin/
```
sudo mv cbc1t /usr/local/bin/
```
6. Login to another shell (or simply type in the command "bash"), and try to run the command "cbc1t"

That should do it. I know it's not using an alias, but it should still do what you want.

---

### Post by ubz on 2007-06-23
> **alan_daniel said:**
> I'm not sure how to do that using an alias, but you could always set up a simple shell script to do it. That should do it. I know it's not using an alias, but it should still do what you want.

Thanks much.  I might use the shell script method although I'd like to try an alias approach if it's doable.  I want to make a number of mplayer radio station shortcuts based on station call signs.
If I use the shell script approach (one radio link per file)  to help keep things organized I presume (please correct me if I'm wrong) it's ok to create a directory in /etc/local/bin/here to hold the radio shell scripts.

---

### Post by alan_daniel on 2007-06-23
As long as the directory that you put them in is in your PATH, it'll be fine. To check if it is, you can run the command "export" and find the "declare -x PATH" part of it

---

### Post by ubz on 2007-06-23
> **alan_daniel said:**
> As long as the directory that you put them in is in your PATH, it'll be fine. To check if it is, you can run the command "export" and find the "declare -x PATH" part of it

Hi, here's the relevant 'export' output.
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:
/usr/bin:/sbin:/bin:/usr/games"
So, making a sub-directory /usr/local/bin/here would be in my PATH correct?
Would mkdir /usr/here/local/bin also be in my PATH?
Thanks for telling me about the export command.

---

### Post by alan_daniel on 2007-06-23
No, the PATH is not recursive. In other words, any sub-directories in any one of those directories listed in the path is not included. The exact directory that you want must be in the path. To add that directory to your path, it must be changed in $HOME/.bashrc

First, you need to open up your .bashrc in your home directory with the app of your choice (vi, etc).

Once that's open, scroll down to the bottom of the file (that's where I generally put things I add myself so that I can always find them), and add this:
```
PATH=$PATH:directory you want
export PATH
```

so instead of "directory you want," just type in the full path of the directory you're putting them in (i.e. /usr/local/bin/here)

Again, open a new shell or run a "bash" command, and it should work

---

### Post by wormser on 2007-06-23
Another simpler option is to create a launcher.  Just right click on the desktop> create launcher> put the command in with the station.  

I did that for RUSH radio (the band, not the wacko)

```
mplayer http://205.188.215.229:8010
```

---

