---
title: "Compiz start"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by whoosh on 2006-09-02
I'm trying to get compiz/XGL to start up when I load up Linux.  I downloaded a python script and put it in /usr/bin, but it still doesn't start up.  I think it has somethign to do with the fact that I type in "thefuture" to start up XGL and not some other terminal command.  Can someone help me?

---

### Post by bulldog on 2006-09-02
You have to set in your session menu,

start-compiz.py

Preferences-sessions and put the line in there and be sure to remove all other lines like the future or compiz-start or what ever points to compiz.

---

### Post by jISh on 2006-09-02
If all you have to do is type "thefuture" to load up XGL, then go to System ->Preferences->Sessions and in the startup program tab add the command.

---

### Post by whoosh on 2006-09-02
Okay, so thefuture works when I put it into the startup sessions, but not compiz-start.py (the file is called compiz-start, not start-compiz).  I don't just want to start up XGL though.  I'm trying to set it up for cgwd.  It says that the compiz-start.py is in the current session but it's not giving me the effects.  When I run compiz-start.py in the terminal I get this:

Traceback (most recent call last):
  File "/usr/bin/compiz-start.py", line 81, in ?
    pixbuf = gtk.gdk.pixbuf_new_from_file("/usr/share/compiz/logo24.png")
gobject.GError: Failed to open file '/usr/share/compiz/logo24.png': No such file or directory

Any ideas?

---

### Post by bulldog on 2006-09-02
You're right about compiz-start.py my mistake.

When you use the python script you should also install cgwd and cgwd-themes.
Then you have to alter your /usr/bin/compiz-start.py like this.

def start_compiz():
	os.system("killall gnome-window-decorator")
	gobject.spawn_async(['cgwd'], \
			     flags=gobject.SPAWN_SEARCH_PATH)
	gobject.spawn_async(['compiz', '--replace', 'gconf'], \
			  flags=gobject.SPAWN_SEARCH_PATH)

Then it should work.

Failed to open file '/usr/share/compiz/logo24.png': No such file or directory
is corrected by installing cgwd and cgwd-themes which gives you nice window decoration.

The following lines must be in your sources.list however I'm not sure about  beerorkid.

##Xgl/Compiz
#deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

---

### Post by whoosh on 2006-09-02
heh thanks a lot.  One last question, how do I install cgwd and cgwd themer?

---

### Post by bulldog on 2006-09-02
When you put the lines from my last posting in your sources.list you should do,

sudo aptitude update
sudo aptitude install cgwd cgwd-themes

or look for them in synaptic using the search,they should be there.

Hope it will work for you,it's running fine here :)

Just saw in synaptic cgwd-themes-extra!!!!!
Look for it there should be three items cgwd--cgwd-themes and cgwd-themes-extra

---

