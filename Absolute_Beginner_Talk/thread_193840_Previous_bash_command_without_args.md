---
title: "Previous bash command without args"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by underwater on 2006-06-10
Is there a way to hit the previous bash command without arguments?

Kinda like !! but with no arguments attached.

That way I could just enter that symbol with my new argument and rerun that command with the new args.  I read through the bash reference manual and didn't see it.  Does it exist?

---

### Post by richbarna on 2006-06-10
You can create a BASH alias for a command :-
If you always run a command with the same set of options, you can have bash create an alias for it. This alias will incorporate the required options, so that you don't need to remember them or manually type them every time. For example, if you always run ls with the -l option to obtain a detailed directory listing, you can use this command:
bash> alias ls='ls -l'

To create an alias that automatically includes the -l option. Once this alias has been created, typing ls at the bash prompt will invoke the alias and produce the ls -l output.

You can obtain a list of available aliases by invoking alias without any arguments, and you can delete an alias with unalias.

---

### Post by underwater on 2006-06-10
No, an alias isn't what I was looking for, unless I made an alias that always would let me hit the previous command and use that command again without args.  

Really what I've always been looking for is something like 

!!

but that doesn't come with arguments attached.  This way I could do a command like

nslookup ubuntuforums.org

and then do the command

!~ google.com


or something like that to do a nslookup of google.com

---

### Post by kabus on 2006-06-10
[QUOTE=underwater]Is there a way to hit the previous bash command without arguments?
[/QUOTE]
```

!:0
```

---

### Post by underwater on 2006-06-11
[QUOTE=kabus]```

!:0
```[/QUOTE]
I tried that already, but I thought that wasn't quite it because it seemed to be echoing out the command.  At first I thought it wasn't what I was looking for, but after your post I see that !:0 does do what I want, it just echos the command in the process for some reason

To show by example

$ echo "foo"
foo
$ !:0 "bar"
echo "bar"
bar



Oh well, close enough for me

---

