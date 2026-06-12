---
title: "Can't get to my Program Files-folder"
date: 2011-10-20
forum: Any Other OS
---

### Post by Avegard on 2011-10-20
Hello!

Got my brand new Mac a few weeks ago and wanted to play some PC games again. Got my hands over a app called Wine who're supposed to do the work with installing an .exe file.

Installation went well, I got the game. It somehow crashes and I need to add some files into the Program Files-folder. Now... How the hell do I get there?

I've tried Google it, I get several answers who says that I should use Terminal to open the folder. No success. Terminal keeps saying "No such directory", I figured I'm maybe typing wrong.

So this is what it looks like in Terminal, a new line looks like this:
*[COLOR="Gray"]Kevins-iMac:~ kevinavegard$[/COLOR]*

I type the following:
*[COLOR="Gray"]Kevins-iMac:~ kevinavegard$ cd /.wine/drive_c/Program\ Files/[/COLOR]*

I get this response:
*[COLOR="Gray"]-bash: cd: /.wine/drive_c/Program Files/: No such file or directory[/COLOR]*

Since I'm totally new to this, I have no clue what to do now. Any idea fellas? Really appreciate some feedback. I want to play this game so badly (:

Thank you on beforehand!

Kind greetings
Kevin

---

### Post by nothingspecial on 2011-10-20
Moved to Other OS/Distro talk.

---

### Post by mcduck on 2011-10-20
```
cd ~/.wine/drive_c/Program\ Files/
```
or:
```
cd /Users/yourusername/.wine/drive_c/Program\ Files/
```
/replace the "yourusername" with your actual user name)

Or if you are currently in your home directory:
```
cd .wine/drive_c/Program\ Files/
```

If you start the path with a "/", that would mean the root of the filesystem, not the directory where you currently are.

---

### Post by Avegard on 2011-10-20
> **mcduck said:**
> ```
cd ~/.wine/drive_c/Program\ Files/
```
or:
```
cd /Users/yourusername/.wine/drive_c/Program\ Files/
```
/replace the "yourusername" with your actual user name)

Or if you are currently in your home directory:
```
cd .wine/drive_c/Program\ Files/
```

If you start the path with a "/", that would mean the root of the filesystem, not the directory where you currently are.

Thank you for your reply. Sadly, none of the codes seems to work. I copied the lines directly from your comment and removed "yourusername" to mine, but sadly it didn't work out.

Any other ideas?

Thanks again!

---

### Post by ubupirate on 2011-10-20
Have you run the initial wine config first?

Open terminal and:

```
winecfg
```

Then:
```
cd ~/.wine/drive_c/Program\ Files
```

---

### Post by Avegard on 2011-10-20
> **ubupirate said:**
> ```
winecfg
```

"Command not found"... Is it me or?

---

### Post by BosnmateSWCC on 2012-07-30
Well I did everything and got to my program files on my terminal.  Now I can't get out of it the Program files to go back to my original terminal.  Any help please

---

### Post by RFS-81 on 2012-07-30
Typing cd ~ should get you back to your home folder, if that is what you mean by original terminal.

---

