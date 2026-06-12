---
title: "Where'd My New Program Go?"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by dpaint4 on 2006-03-08
I already know this is a 'stupid' question. In fact it's so stupid that I think everyone must just take the answer for granted and never talk about it anywhere, so I'm going to have ask it and sacrifice my pride for an answer. Be nice, okay?

Look, I love the cute little Package Manager called 'Add Applications' or whatever. That's aimed straight at me. It's graphical and adds the program I select to all appropriate access spots in my system.

However, recently I needed to use a more grown-up package manager to add a 7zip Utility to my system, and it worked fine as far as I can tell, besides that I've done whole system searches and can't find anything even relating to the name of the package, which was, incidentally, "p7zip".

In the past I've used this same package manager, and it installs a package, usually successfully, after which I go on a wild hunt all over my system by hand and through the search utility to find whatever was installed.

I thought for a while that they were usually installed in user/bin.

There has got to be some incredibly simple other way that people are doing this that I just haven't found out yet. Command line? That's fine. Throw it at me. I'm cool with that. But where do the new packages GO?

---

### Post by Klaidas on 2006-03-08
How did you search for the program?

---

### Post by taurus on 2006-03-08
If you install a program using synaptic or apt-get, then it's more likely it will be in /usr/bin!  However, if you build it from source, then chances are it will be in /usr/local/bin.  To find a program on your system, run
```

sudo find / -name filename -print

```

---

### Post by engla on 2006-03-08
If you are in synaptic, select an installed package and select 'properties'

Look in the tab that says installed files. Yep, that's a list of all files that come from the package and where they are.
Normally the executables are easy to find, they are in /usr/bin but could be in any .../bin/ folder

---

### Post by IYY on 2006-03-08
In general, the best approach is to enable the Debian menus and search for the program in them (I think Automatix does this).

---

### Post by dpaint4 on 2006-03-08
[QUOTE=IYY]In general, the best approach is to enable the Debian menus and search for the program in them (I think Automatix does this).[/QUOTE]

Thanks new Ubuntu friends. Well, if there's one thing I'm comforted by it's that I guess I haven't been doing this 'wrong'. Sounds like it's just a little complicated, but that's fine.

I've saved your replies to a text file and sent it to my home account so I can try this stuff when I get off work. I really appreciate the replies.

Thanks again.

---

### Post by dpaint4 on 2006-03-08
K. I found a binary and a shell script thanks to your advice. The shell script seems to do nothing more than activate the binary. The binary seems to do nothing at all. I try to execute it like any other binary and the result is nill.

My dream would be for the 7z program to end up in my context menu so I can just right-click and decompress my 7z files.

I checked the permissions and I'm not the owner of either the script or the binary. Root is. Funny that these installed to my user folder and yet I don't have persmissions.

I understand the role of root in Ubuntu, so you don't have to tell me about that, but is there anyway I can own these files so that I can run them/add them to my menus etc? Any advice?

---

### Post by dpaint4 on 2006-03-08
HA! Sorry for *another* post, but I just figured out that this is a command line tool. No GUI or shell integration. I'm a little bummed about that, but I'm still thrilled to have access to my 7z files!

Thanks for helping me find it and for tollerating my questions!!!

---

### Post by engla on 2006-03-08
[QUOTE=dpaint4]My dream would be for the 7z program to end up in my context menu so I can just right-click and decompress my 7z files.[/QUOTE]
It's actually pretty easy to make it end up in your context menus in nautilus if you know the shell command. 

I'll take an example I know -- gzip.
The command to decompress files is 'gunzip', so if I want to unpack these in nautilus I do the following:

Right click on any file with the right filetype (this case **.gz**)
Select Open With > Open with other application
A window opens, click the arrow at the bottom "Use custom command"
enter **gunzip**

Now this should be available for all files of this type in the future. All you have to do is adapt the things in **bold** to 7zip things.

---

