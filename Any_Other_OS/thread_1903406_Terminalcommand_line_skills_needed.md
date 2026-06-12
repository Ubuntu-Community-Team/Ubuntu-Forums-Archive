---
title: "Terminal/command line skills needed"
date: 2012-01-02
forum: Any Other OS
---

### Post by I_can_see_the_light on 2012-01-02
Hi! I wasn't sure about where to ask this so apologies if it's in the wrong section.

I'm running CrunchBang wich is based on Debian and my screensaver is XScreenSaver. When playing a movie in Gnome Mplayer the screensaver activates unless I edit  [FONT="Courier New"]~/.mplayer/config[/FONT]  and enter (according to [XScreenSaver faq)]("http://www.jwz.org/xscreensaver/faq.html#dvd") ```
heartbeat-cmd="xscreensaver-command -deactivate **>&- 2>&- &**"
```
My question is, what does the part in bold mean?

---

### Post by kalfusisagod on 2012-01-02
I think the ampersand (the & symbol) puts the task in the background. I'm not sure about this context though. So if you wrote
```
mv largefile.txt largefile2.txt&
```

Then this would put it into the background of the terminal so the command prompt would show up right away, and to list background terminal tasks, you can use 
```
ps
```
for processes or
```
jobs
```
Anyone else?

---

### Post by chipbuster on 2012-01-02
[http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

Looks like you're telling it to close both stdout and stderr with the first two. Wonder if that's the same thing as pointing it to /dev/null?

---

### Post by kalfusisagod on 2012-01-02
Oh and I forgot to mention, I think the 2> means that it goes to the error output. Linux has several outputs. 
> standard output
1> standard output
2> error output

For example if your typed
```
ls > files.txt 
```
Then this command would list the current directory and put it into a text file called files. If you typed
```
ls /fakedirectory 2> files.txt 
```
Then this would put 
```
ls: cannot access /fakedirectory: No such file or directory
``` into a file called files.txt. This would not happen with a normal > option because error output in not mixed with standard output. Hope this helps.

---

### Post by Paddy Landau on 2012-01-02
The ampersand on its own means to put it into the background as an asynchronous background task. Thus, that's the final ampersand that does it.

The symbol "[FONT=Courier New][SIZE=2]>[/SIZE][/FONT]" means to redirect output. There are two usual outputs, one being stdout or 1, which is normal output, and the other stderr or 2, which is error messages.

Thus: "[FONT=Courier New][SIZE=2]1>&-[/SIZE][/FONT]" means to send stderr to something called "[FONT=Courier New][SIZE=2]&-[/SIZE][/FONT]" (more on that in a moment) instead of its usual terminal; and "[FONT=Courier New][SIZE=2]2>&-[/SIZE][/FONT]" means to also send stderr to "[FONT=Courier New][SIZE=2]&-[/SIZE][/FONT]".

"[FONT=Courier New][SIZE=2]>&-[/SIZE][/FONT]" is shorthand for "[FONT=Courier New][SIZE=2]1>&-[/SIZE][/FONT]".

Incidentally, "[FONT=Courier New][SIZE=2]&>[/SIZE][/FONT]" is shorthand for "*both 1 and 2 >*", thus "[FONT=Courier New][SIZE=2]>&-1 2>&-[/SIZE][/FONT]" could be shortened to "[FONT=Courier New][SIZE=2]&>&-[/SIZE][/FONT]".

Confused yet?

I do not quite understand what "[FONT=Courier New][SIZE=2]&-[/SIZE][/FONT]" means, but I think it means to send output to the owning variable; in this case we don't know what it is, because it gets passed to XScreenSaver.

You can read more about redirection by using the command:```
man bash
```and searching for REDIRECTION. You can also find more about background jobs in the same manual. There is a copy of the [bash manual on-line]("http://www.gnu.org/software/bash/manual/html_node/") if you find that easier.

---

### Post by oldos2er on 2012-01-02
Moved to Other OS/Distro Talk.

---

### Post by I_can_see_the_light on 2012-01-02
Ok, thanks to all three of you.

This is output from running the command in the terminal:
```
isen@crunchbang:~$ xscreensaver-command -deactivate >&- 2>&- &
[1] 9007
isen@crunchbang:~$ xscreensaver-command -deactivate >&- 2>&- &
[2] 9008
[1]   Done                    xscreensaver-command -deactivate 1>&- 2>&-
isen@crunchbang:~$ 

```

This is what it looks like without redirecting, just putting it in the background.
```
isen@crunchbang:~$ xscreensaver-command -deactivate &
[1] 9018
isen@crunchbang:~$ xscreensaver-command: not active: idle timer reset.


```It looked like I could continue using the terminal but then the *idle timer reset* message interrupted and stole the prompt. Anyway, I'm marking this thread as solved :)

---

### Post by kalfusisagod on 2012-01-02
A word of advice, go out and get a good book on the terminal, it's a lifesaver! The terminal will be 90 percent the same across most distros unlike KDE, Gnome, and Unity with their constant changes. A good book I'd recommend is "A Practical Guide to Linux Commands, Editors, And Shell Programming" by Mark Sobell.

---

### Post by sisco311 on 2012-01-02
[n]<&word is used to duplicate input file descriptors and [n]>&word is used to duplicate output file descriptors. If *word* evaluates to -, then file descriptor *n* is closed.

>&- or 1>&- closes file descriptor 1 (stdout) 
and
2>&- closes file descriptor 2 (stderr)

See:```

man bash | less +/" +Duplicating File Descriptors"
man bash | less +/"^REDIRECTION"

```

[http://mywiki.wooledge.org/BashGuide/InputAndOutput](http://mywiki.wooledge.org/BashGuide/InputAndOutput)
[http://wiki.bash-hackers.org/syntax/redirection](http://wiki.bash-hackers.org/syntax/redirection)
and the POSIX specification:
[http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_07](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_07)

Another option would be to redirect stdout & stderr to /dev/null.
BASH:
```

command &> /dev/null
```
Note: this is not standard, so I'd avoid it in scripts. But it's shorter than the POSIX form, hence it's handy in an interactive BASH shell.

The POSIX form is:
```
command > /dev/null 2>&1
```

---

### Post by I_can_see_the_light on 2012-01-02
> **kalfusisagod said:**
> A word of advice, go out and get a good book on the terminal, it's a lifesaver! The terminal will be 90 percent the same across most distros unlike KDE, Gnome, and Unity with their constant changes. A good book I'd recommend is "A Practical Guide to Linux Commands, Editors, And Shell Programming" by Mark Sobell.

Yeah, that's on my "todo list". I've got one in a Swedish translation/rework from Gareth Anderson's *GNU/Linux Command-Line Tools Summary* but I'd like to have another one which digs a little deeper. I will have a look at the one you mentioned.

---

### Post by I_can_see_the_light on 2012-01-02
> **sisco311 said:**
> Another option would be to redirect stdout & stderr to /dev/null.
BASH:
```

command &> /dev/null
```
Note: this is not standard, so I'd avoid it in scripts. But it's shorter than the POSIX form, hence it's handy in an interactive BASH shell.

The POSIX form is:
```
command > /dev/null 2>&1
```
OK, that's good to know.


> **sisco311 said:**
> [http://mywiki.wooledge.org/BashGuide/InputAndOutput](http://mywiki.wooledge.org/BashGuide/InputAndOutput)
[http://wiki.bash-hackers.org/syntax/redirection](http://wiki.bash-hackers.org/syntax/redirection)
and the POSIX specification:
[http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_07](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_07)

Thanks for the links, and the ones in your sig :)

---

### Post by Paddy Landau on 2012-01-03
> **sisco311 said:**
> >&- or 1>&- closes file descriptor 1 (stdout)
2>&- closes file descriptor 2 (stderr)
&> ... is not standard
Thank you for your clarifications -- much appreciated.

---

