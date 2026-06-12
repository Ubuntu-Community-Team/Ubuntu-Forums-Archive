---
title: "[SOLVED] Ruby text editors and vim"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by *grin* on 2007-11-25
I'm as green as a cut-corner rizla-paper pack (in linux, ubuntu and programming) so please be gentle with my enthusiasm and detailed in your instructions! :-

Loving the Ubuntu experience and thinking Ruby looks cool, let's have a go.  I've been trying things in my terminal but I would like the visual feedback of a text editor with syntax highlighting and indenting.  I don't want a full-on IDE, which I feel will interfere with my learning at this stage. 

I've looked at loads of threads for some inspiration.  Jedit doesn't seem interested in installation - neither does RDT,   Mondrian only works with FXRuby 1.2.4 or FXRuby 1.2.6.  Eric is way too much.     

Looks like vim should be my answer (never seen it though).  I installed vim-full from synaptic but, um, I can't seem to find it?!  I did ls -a in my terminal at root and can't find a reference to vim either.  What a numpty!

-Should I use something else?
-Where has vim gone?
-If I use vim is there anything else I should do with vim to make it work properly with Ruby?

Thanks all

(Hoping I'm not going to end up feeling TOO embarrassed).

---

### Post by Taboo Mirage on 2007-11-25
Hello there.

Vim is a command-line text editor and can be very confusing and difficult to get used to.  Executing this, for example from the command line, will open up the text editor:

```
vi testtextfile
```

Commands are not executed as you'd expect in many of the graphical text editors.  If you really do want to learn vi commands you could check out sites like [this](http://www.tuxfiles.org/linuxhelp/vimcheat.html) which give an overview of the commands you need to use to accomplish things.

As for other editors, have you actually taken a look at the editor included within GNOME called gedit?  Go to Applications > Accessories > Text Editor and take a look as to whether or not that suits your needs.  It's a lot more user-friendly than vim and it offers syntax highlighting for a multitude of different languages.  I believe this would suit your needs more.

---

### Post by *grin* on 2007-11-25
Thank you!  I did try Gedit briefly but was unconvinced - I'll go back and try and make friends with it again.

---

