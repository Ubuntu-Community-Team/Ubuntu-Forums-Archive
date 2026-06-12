---
title: "How do I run a .sh file?"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by Doc.Caliban on 2005-10-31
I've given myself rwx rights to it, but when I try to run it I get, "command not found"

-Doc

---

### Post by 23meg on 2005-10-31
Try running it with the "sh" prefix.

```
sh /path/to/script.sh 
```

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=23meg]Try running it with the "sh" prefix.

```
sh /path/to/script.sh 
```[/QUOTE]

I tried with and without.

---

### Post by 23meg on 2005-10-31
Maybe the script initializes but there's a command in it that is "not found"? Can you paste the exact error message you get? 

Also try putting the script path inside double quotes.

---

### Post by xmastree on 2005-10-31
[QUOTE=Doc.Caliban]I've given myself rwx rights to it, but when I try to run it I get, "command not found"[/QUOTE]You need to tell the system where the script is.
Assuming it's in your home directory, it's not enough to CD to that directory and type the script name, the system will only look on the path, which doesn't include your home.
To run it from within the directory, type ```
./scriptname.sh
```

---

### Post by Doc.Caliban on 2005-10-31
That was the exact error.  The name of the scipt and "command not found"

I renamed the script, could that be the problem?  (no, I did not change the extension.)

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=xmastree]You need to tell the system where the script is.
Assuming it's in your home directory, it's not enough to CD to that directory and type the script name, the system will only look on the path, which doesn't include your home.
To run it from within the directory, type ```
./scriptname.sh
```[/QUOTE]

That did it.

I'm not clear on why thouhg.  I had it in a directory outside of my home tree.  Why would attempting to execute it from the directory it's in not work?  Coming from DOS 4 days, that's really odd to me.  (Been using linux for 2 days now.)

-Doc

---

### Post by xmastree on 2005-10-31
[QUOTE=Doc.Caliban]Why would attempting to execute it from the directory it's in not work?[/QUOTE]Because the system **only** looks on the path for programs, not even in the current directory. Coming from DOS, that does seem strange but you soon get used to it.

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=xmastree]Because the system **only** looks on the path for programs, not even in the current directory. Coming from DOS, that does seem strange but you soon get used to it.[/QUOTE]


Ah, I get it.  I didn't quite come away with that from the previous post.  VERY important to know!

Where can I / should I ever, edit the path variable?

---

### Post by xmastree on 2005-10-31
[QUOTE=Doc.Caliban]Where can I / should I ever, edit the path variable?[/QUOTE]Erm... I don't know. :rolleyes: 
I guess if you have a lot of scripts, and like to keep them together it could be useful to add that directory to the path.
I suspect you edit ~.bash_profile but I'm not sure.

I think the answer will be in [here]("http://www.ubuntuforums.org/search.php?searchid=2317124") somewhere though.

---

### Post by 23meg on 2005-10-31
You can also make aliases for your often used scripts / commands. See here:
 [http://www.linuxcommand.org/wss0020.php#aliases](http://www.linuxcommand.org/wss0020.php#aliases)

---

