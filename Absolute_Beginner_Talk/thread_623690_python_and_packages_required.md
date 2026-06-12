---
title: "python and packages required"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by raninaki on 2007-11-26
Hello evereyone! My name is rania and I am from greece!

I am an adsolute beginner  :) and I want to ask what should I do to program in python.

What packages are required?? 

I have a very imprortant project at school! I have to program at command line at firt and then with graphics! 

Thank you in advance!

P.S. excuse my english but it's been a long time since I last practiced it. :)

---

### Post by Xavieran on 2007-11-26
Python is installed with ubuntu by default.
To access it type python in any terminal,command prompt...

You will probably want an IDE and there are plenty available in the
synaptic repositories.I chose DrPython first but as you get more advanced you can use different IDE's
search google for Python Tutorials and you will find plenty.
I found [Dick Baldwin']("http://www.dickbaldwin.com/tocpyth.htm")s a very thorough introduction to datatypes and you could do [Alan Gaulds]("http://www.freenetpages.co.uk/hp/alan.gauld/") .

Hope you have fun!

P.S. if you want a few sample scripts to begin with I'd be happy to share them.
Just PM me or ask for them in this thread...:)

---

### Post by luisfcup on 2007-11-26
Just go to the the application menu -> Add/Remove programs, and look for IDLE, it should be in the development section. Check if it is the Python 2.5 version.
And thats it :) You can start Python IDLE in Application -> development section, or you can star the python in command line, simply righting "python" (without the quotes) in a terminal.

EDITED: Sorry, I though python didn't came with Ubuntu installation, I actually installed IDLE before trying the command line. You can also try emacs to right python code, if you don't like the python editors available.

---

### Post by raninaki on 2007-12-14
Thanks very much for your help!!

I have one more question!!

I use Kdevelop scripting because I was adviced to do so by my superiors :)

I wrote several programmes in python that worked fine!! But I cannot run any programmes with graphics. The programme compiles but no window appears by this ```

import pygtk
pygtk.require('2.0')
import gtk

class Base:
	def __init__(self):
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.show()

def main(self):
	gtk.main()
	print __name__
	if __name__ == "__main__":
		base = Base()
		base.main()
``` 

Can anyone help me?? Thanks in advance!!

---

