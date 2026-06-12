---
title: "Opening a console in a specific directory"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by dude87 on 2007-01-11
Is there a way to open a console in a specific directory?  Some of my directory structures have long, convoluted names and using "cd" to navigate to a specific directory can be a long process full of typos, etc.  My previous Linux distro (Xandros) had an option to right-click on a directory in their file manager and select "open console window here", is there anything like that in Ubuntu?  I'm using release 6.10.

thanks

---

### Post by Lord Illidan on 2007-01-11
> **dude87 said:**
> Is there a way to open a console in a specific directory?  Some of my directory structures have long, convoluted names and using "cd" to navigate to a specific directory can be a long process full of typos, etc.  My previous Linux distro (Xandros) had an option to right-click on a directory in their file manager and select "open console window here", is there anything like that in Ubuntu?  I'm using release 6.10.

thanks

Did you know that if you are typing in bash, and you press TAB you can autocomplete?

So, let's say I want to go to /home/foo/documents

And I am in /home/foo already.

I just need to type in cd doc, then press TAB, and it will autocomplete it for me.

There are also scripts for Nautilus to open terminal windows.

---

### Post by xmastree on 2007-01-11
I'm sure there's a nautilus script to open a terminal in a directory, but that would mean navigating to that directory first.

---

### Post by dude87 on 2007-01-11
> **Lord Illidan said:**
> Did you know that if you are typing in bash, and you press TAB you can autocomplete?

So, let's say I want to go to /home/foo/documents

And I am in /home/foo already.

I just need to type in cd doc, then press TAB, and it will autocomplete it for me.

There are also scripts for Nautilus to open terminal windows.

Okay, the TAB thing helps, although a lot of my directories have similar names up until the last few characters.  Where can I find the Nautilus scripts?

thanks

---

### Post by xmastree on 2007-01-11
> **dude87 said:**
> Where can I find the Nautilus scripts?

thanks

[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

The instructions are all there, have fun.

Edit: here it is:

```
#!/usr/bin/perl -w
#
# Open terminal here
#
# Nautilus script that opens a gnome-terminal at the current location, if it's
# a valid one. This could be done in shell script, but I love Perl!.
#
# 20020930 -- Javier Donaire <jyuyu@fraguel.org>
# http://www.fraguel.org/~jyuyu/
# Licensed under the GPL v2+
#
# Modified by: Dexter Ang [thepoch@mydestiny.net]
# 2003-12-08: Modified for Gnome 2.4
#		- Added checking if executed on Desktop "x-nautilus-desktop:///"
#		  so that it opens in /home/{user}/Desktop

use strict;

$_ = $ENV{'NAUTILUS_SCRIPT_CURRENT_URI'};
if ($_ and m#^file:///#) {
  s/%([0-9A-Fa-f]{2})/chr(hex($1))/eg;
  s#^file://##;
  exec "gnome-terminal --working-directory='$_'";
}

# Added 2003-12-08 Dexter Ang
if ($_ == "x-nautilus-desktop:///") {
  $_ = $ENV{'HOME'};
  $_ = $_.'/Desktop';
  exec "gnome-terminal --working-directory='$_'";
}

```

---

### Post by dude87 on 2007-01-11
Thanks, I'll play around with this but it should do the trick.

---

### Post by xmastree on 2007-01-11
Alternatively, looking at that last line in the script, you see the answer.

```
gnome-terminal --working-directory='/foo/bar'
```

I just made a launcher with the above as the command, and it worked.

---

### Post by CroEragon on 2007-01-11
You can use KDE, if you dont want KDE you can still use Konqueror. It is default file manager and browser in KDE and got option right click ->Actions->Open this folder in terminal

---

### Post by pcomelade on 2007-01-11
try:

$ FOLDER=/path/to/a/long/directory/
$ ls $FOLDER


Hope it helps!

M;

---

