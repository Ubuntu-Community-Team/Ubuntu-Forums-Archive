---
title: "How to make a link to an exec that have options or arguments"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by NeoRc on 2005-11-24
For example, I wanna make a link to "mpg123 -q abc.mp3", how can I add the option "-q" and the argument "abc.mp3" to the link.
Thx for any suggestions.

---

### Post by oskude on 2005-11-24
how about "mpg123 -q abc.mp3" as the command ? :)
then again, what link and where ?
what have you tried ?
what didnt work ?

---

### Post by Ruso on 2005-11-25
I dont know if I understood u right but u can make this.

Open ur favorite texteditor.

write this:

```

#!/bin/bash
mpg123 -q abc.mp3

```

Save it for example as **mpabc**, or whatever u want.
then 
```
chmod +x mpabc
```

and copy it to the /usr/bin for example 
```

cp mpabc /usr/bin
```

Then just by typing mpabc u will run the mpg123 -q abc.mp3 command.

Or u can make an Alias
```

alias mpq='mpg123 -q abc.mp3'

```
You can put this line in ur .bash_profile file in the home direcory. So when u log-in with ur account this alias will be enabaled and you can type mpq for running the command "mpg123 -q abc.mp3"

If I did understand you wrong then sry. :( :(

---

### Post by NeoRc on 2005-11-25
Actually, hmm, I just wanna try something for fun:) 
I noticed the command *gvim* in the folder /usr/bin is just a link, and it link to the command *vim* in the same folder. Seems like they should have the same effort, but, you know, the two are not the same. *gvim* is the GUI version of *vim*, it starts a new window, *vim* does not.
I have a look at the man page of *vim*, it said that the *gvim* is as same as *vim -g*. So I think there's must a way to make a link to a command with options, *gvim* is linked to *vim -g*.
Must take *vim -g* as one argument to pass it to *ln*

---

### Post by msr7x57 on 2005-11-25
WRT your post that "gvim" is the same as "vim -g" - you're right, but I suspect that if you read the source for vim, you'll find something that checks command line options and then branches depending on what they are.

In this case the "alias" route is the way to go  ;-)

---

### Post by oskude on 2005-11-25
[QUOTE=NeoRc]Actually, hmm, I just wanna try something for fun:) 
I noticed the command *gvim* in the folder /usr/bin is just a link, and it link to the command *vim* in the same folder. Seems like they should have the same effort, but, you know, the two are not the same. *gvim* is the GUI version of *vim*, it starts a new window, *vim* does not.
I have a look at the man page of *vim*, it said that the *gvim* is as same as *vim -g*. So I think there's must a way to make a link to a command with options, *gvim* is linked to *vim -g*.
Must take *vim -g* as one argument to pass it to *ln*[/QUOTE]ok, i understand you 100% now.

i made some tests with linking (ln -s) vim, and i noticed if the link target has a "g" as the first character it starts "vim -g", and all other targets started only "vim" :confused: 
but dunno what makes this happen, and i would be interested on this too :)

to your problem, i looked at "man ln", but still made a TaE(Trial and Error) test like```
sudo ln -s "/usr/bin/vim -g" /usr/bin/justatest
```and the link didnt work (but didnt expect it to)

so your best bet would be an "alias" or script, like "Ruso" suggested

cheers
osku[de]

edit:
doh, i somehow didnt read the post (from msr7x57) before this post. so its a "feature" of vim that if the link name has "g" as the first char, it starts "vim -g", ok.

---

### Post by ssam on 2005-11-25
you could make an alias.

for example is you use
```
ls -l
```
a lot you might want to alias it to
```
ll
```
if you run
```
alias ll="ls -l"
```
then you can run things like
```
ll /etc
```

you can then put the alias line in you .bashrc to make it work for every new terminal you start.

for more complex examples you can make a bash script and use $1 for the argument. eg
```

#!/bin/bash
echo "playing $1 in backgroud"
mpg321 -q $1 &

```

which should start the file playing an drop you back to the terminal (thats off the top of my head, so it may not work)

---

### Post by NeoRc on 2005-11-25
[QUOTE=msr7x57]WRT your post that "gvim" is the same as "vim -g" - you're right, but I suspect that if you read the source for vim, you'll find something that checks command line options and then branches depending on what they are.

In this case the "alias" route is the way to go  ;-)[/QUOTE]
I have seen the source, and made some tests. When I launch an app thru the link, the variable *argv[0]* is the name of the link, not the app's name itself (when, of course, the link's name is different from the app's name). Though I still don't know how it should be that, but it surely explain what I asked.
Thx for all the replies:)

---

