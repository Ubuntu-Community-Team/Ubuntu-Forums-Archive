---
title: "[SOLVED] LS command"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-10-31
I was going mad last night. Why wont the following work?

ls -R *.jpg

or

ls *.jpg -R

I want to get a list of all jpgs in a dir tree. :confused:

---

### Post by PmDematagoda on 2007-10-31
Why don't you try 

```
ls *.jpg
```

?

---

### Post by Torajima on 2007-10-31
What you want is:

> ls - R */*.jpg

---

### Post by ByteJuggler on 2007-10-31
Hmm, careful here.  ls -R */*.jpg won't find all .jpg files either.  

**There's a subtle but crucial difference here between how Windows command prompt would operate and how the Linux/Unix shell operates that can drive you crazy if you're not aware of it/how it works.**  To explain: The Windows command prompt/shell does no wildcard processing itself.  That is, if you type

```
Dir *.jpg /s
```

... the command line passed to the "dir" program is "*.jpg /s"   It is then up the "dir" command program to process/parse those parameters and expand them to the result you see, which is to recursively search for files matching the wildcard name "*.jpg"

However, on Unix/Linux under the shell, things work slightly differently:  Wildcard expansion (with rare exceptions) are considered to be the responsibility of the shell itself.  That is, **unless you explicitly prevent the shell from expanding wildcards, no such wildcard file specifications will ever reach a command/program you enter, as they would get expanded by the shell prior to passing to the program/command in question. ** 

So for example, suppose you've got "a.jpg" and "b.jpg" in the current folder, and you then enter :

```
ls -al *.jpg 
```

Two things happen, firstly the shell expands "*.jpg" into "a.jpg b.jpg", and then only is the commandine passed to the "ls" command, in effect becoming:

```
ls -al a.jpg b.jpg 
```

So, you might then ask, what is the point of the "-R" switch for the "ls" command?   Well, -R actually only concerns itself with parameters that are directories, and only then, will it list that subdirectory recursively (and I might add, with no filename filter in place.)  On Unix, the expectation would be that if you then want to cut the output down, you'd use another tool specifically for that purpose (for example "grep".)  

So in the end you probably actually want something like this:

```
ls -R | grep "\.jpg"
```

The "|" means "pipe into", so the ls command pipes its output, one entry per line, into the "grep" program (which searches for things using a regular expressoin syntax) which then outputs the results.  Aside: The "\" before the "." is to mark the dot do be treated literally, as it normally means "match any character in a grep regular expression.  Since we want grep to match the actal "." character, we have to escape it with the "escape" character "\", which you'll see below in a moment as well.  The grep command can be read/translated as "Print me all lines of text coming from the standard input, that contains the literal string ".jpg".

There is another probably more elegant alternative, the "find" command.  The "find" command can be used to find files (it is recursive by default), and you'd use it as follows:

```
find . -name \*.jpg
```

This means 'Please find me, from the current directory [e.g. "."], all files matching the following case-sensitive [e.g. "-name"] wildcard "*.jpg"  '  The "\" before the * is to *escape* (mark as special) the following "*" character to prevent the shell from doing its thing again as explained above, and ensuring the string "*.jpg" is passed to the find command unchanged.

As an aside:  If you were to run the command "find . -name *.jpg"  (e.g. omitting the \) then this may or may not work, depending on whether you have any jpg files in your current folder... If you *don't* then the shell will try to expand the *.jpg in the current folder, find that it can't (or that the expansion result is empty) and then pass the string "*.jpg" to find to process itself (rather than passing the empty expansion).   However, if there is at least one jpg file in the current folder (e.g. say "a.jpg", then the shell will expand *.jpg into a.jpg, and your find command will suddenly in fact be looking for "a.jpg" recursively in the current folder... probably not what you're expecting!)  If this is unclear then please post and I'll elaborate with an example you can work through yourself.

So anyway, moral of the story is, remember to escape wildcards for commands that accept them, and be aware of the way the shell processes wildcards as it's rather more sophisticated than in Windows...  Play around and do a few experiments to make sure this difference is understood, and if you have more questions post back.

---

### Post by Rinzwind on 2007-10-31
ByteJuggler that's one heck of an excellent reply. :)

---

### Post by dgrafix on 2007-10-31
It is indeed! :KS:KS:KS

Thanks ByteJuggler, i think will print this and hang it on my wall until assigned to the old grey ram.

---

### Post by ByteJuggler on 2007-10-31
No problem, glad to help.  

(Please remember to mark your thread as answered/solved (under "Thread tools") once you're happy everything's cleared up BTW)

---

