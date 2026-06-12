---
title: "newbe to newbe guide to linux commands - a documentation of a learning proccess"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by yman on 2006-08-03
hello fellow newbs,
I'm a newbe, but I don't like it very much, so I took of the library this 800+ pages book from 1999 called "mastering linux" by Arman Danesh, skipped to page 220 and started learning the basic linux commands. I wrote down some of my progress in OOo writer, and here the results. I hope this helps other newbies get on the road to becoming advanced users.

each command listed here is devided into 4 main parts:
[LIST=1]
[*]the command and what it stands for.
[*]a general description of what it does.
[*]an explanation about how to use the command.
[*]examples with explanations and additional information.
[/LIST]

here are links to the files:
[in open office text format]("http://www.orangejew.com/ubuntu/newbe_to_newbe_guide_to_linux_commands-a_documentation_of_a_learning_proccess/newbe_to_newbe_guide_to_linux_commands-a_documentation_of_a_learning_proccess.odt")
[in PDF format]("http://www.orangejew.com/ubuntu/newbe_to_newbe_guide_to_linux_commands-a_documentation_of_a_learning_proccess/newbe_to_newbe_guide_to_linux_commands-a_documentation_of_a_learning_proccess.pdf")
[in word format]("http://www.orangejew.com/ubuntu/newbe_to_newbe_guide_to_linux_commands-a_documentation_of_a_learning_proccess/newbe_to_newbe_guide_to_linux_commands-a_documentation_of_a_learning_proccess.doc")

---

### Post by ironfistchamp on 2006-08-03
That is brilliant. Very useful. Well done :-D

---

### Post by ColdDeath on 2006-08-03
Lookin' good ;)

Just a suggestion - Why not make the titles bold? IT would make them stand out more.

Also is it completely finished? Because it just ends with "Less -" and no text for it.

Good work so far.

---

### Post by cantormath on 2006-08-03
Rock on,

However, there are way better books out there, you know this right?

---

### Post by Brunellus on 2006-08-03
I should say that, for the technically-inclined newbie, the manual pages for each of the command-line utilities are usually a good thing to read.  
```

man $COMMAND

```
where $COMMAND is the command you want to learn about.

---

### Post by yman on 2006-08-03
I wrote the "more" command this morning, but being weak as I am at the moment, I was afraid I would try to summarize to cover grounds fast rather than being through. I think I already violated my guidlines with "more".
if you want to write commands to be added to the guide then past them in this thread. I'll look them over and use them. when writing bear in mind these guidlines:
1. each command should be as stand alone as possible. you should not rely on any preknoledge of the reader, including from the guid itself.
2. be through. don't spare words in making a point clear.
3. keep in mind that your writing to newbies. make zero assumptions on preknoledge and technical knoledge.
4. maintain the structure of the commands.
5. yman is the narrators username. zman is the other user. yman-Laptop is the PCs name.
6. try to write in a "professional" way most of the time, but not all the time.
7. everything you mention should have an example with an explanation.

---

### Post by yman on 2006-08-03
> **cantormath said:**
> Rock on,

However, there are way better books out there, you know this right?
sure I do. I just never encountered a single manual in my life that was really 100% copatible with newbies for simple reasons that experts wrote it. experts need to emulate newbie thinking, and even though they do a good job its still a little bit crancky. by not being an expert I dont have to lower mayself to a novice level, I'm already there.

or maybe you meant books better than "mastering linux"? all the books about linux in my library are as old as it, and its one of the two largest ones, so thats why I chose it. Its written well enough for me.

> **Brunellus said:**
> I should say that, for the technically-inclined newbie, the manual pages for each of the command-line utilities are usually a good thing to read.  
```

man $COMMAND

```
where $COMMAND is the command you want to learn about.

I find that the "man pages" have too much information for me to deal with without prep. plus, the ones I looked out seem to assume you know how to write commands. the goal of my writing is to make people familiar enough with the command line to be able to easily follow technical instructions and to learn new commands by using "man pages". but I'm not planing to stop at that, I want to write down in this anything I learn, like a notebook. you write in your notebook summaries of the lessons even though you can read them in your textbook. it helps you remember (so maybe all newbies should write such a guide), plus, I experiment with every command that I list and that way I get familiar with them.

---

### Post by Brunellus on 2006-08-04
While I agree that the man pages can be rather tough to read occasionally, they are often a good place to start.  Most manual pages have a standard structure:
**
Program name 
Brief description 

command-line syntax, with all options (this can often look like gobbledegook to newbies, but take heart)

Documentation
Examples (in some man pages)

**

Frankly, the biggest step, as you're finding out, is to get past the mindset that the man pages are impossible to figure out.  They're not.  All you need to do is think that it is possible, and that's half of getting to understanding it.

One learns a little at a time.  I'm constantly learning new things about linux.  The trick is to be open to learning them.  It looks like you're well on your way.  Good luck.

---

### Post by AsYouWish on 2006-08-04
While man pages are fairly usefull to me (total n00b), they dont show you how to do things like "| more". I knew some sort of command existed to do this, but I spent alot of time looking in the man page for ls thinking is was an option. Didnt know it was a different command. And would not have known to pipe to it.

Thats why guides and books (and Google to find them) are so helpful when starting out. So thanks to yman.

---

### Post by Brunellus on 2006-08-04
piping and input/output redirection are the greatest things about the bash shell, and the things least obvious to newbies.  I should recommend a smaller book, called "How Linux Works" by Brian Ward (No Starch Press):  good, basic overview of the shell (and how to love it), plus a lot of work on how networking works, how linux boots, etc.  A good, accessible reference that doesn't insult your intelligence or thunder over your head.

---

### Post by yman on 2006-08-04
> **Brunellus said:**
> piping and input/output redirection are the greatest things about the bash shell, and the things least obvious to newbies.  I should recommend a smaller book, called "How Linux Works" by Brian Ward (No Starch Press):  good, basic overview of the shell (and how to love it), plus a lot of work on how networking works, how linux boots, etc.  A good, accessible reference that doesn't insult your intelligence or thunder over your head.

what year is it? is it still in print? I'll look it up in my library.

about the man pages: I really tried understanding how to use a command just by reading it's structure and the description of what it does, but I can't, it's too difficult for me.

---

### Post by Brunellus on 2006-08-04
it should still be in print;  it published in 2004, and it's still easily finadable.  

Hang in there and keep at it.  it'll all be worthwhile.

---

### Post by yman on 2006-08-04
> **Brunellus said:**
> it should still be in print;  it published in 2004, and it's still easily finadable.  

Hang in there and keep at it.  it'll all be worthwhile.

my library only has books about linux from 2001 and earlier, but I'll go look anyway.

edit: I checked. the newest book they have is "Linux for dummies 3rd edition" from 2001. all the rest are from 1997-1999. there are also about 3 books about specific distributions.

we have a few 20 year old books about unix, are they any good for linux?

---

### Post by cleverselfreferentialname on 2006-08-05
A good entry for less might be 

```
Less is a utility, similar to more, but considerably more advanced, since it allows one to move up, down, left and right with the arrow keys. Putting | less (that is, piping it through less) will make the output of any program have less support.
```

Distributed under the [Anti-Microsoft Public License]("http://wonderland.illtel.denver.co.us/texts/ms-public-licence.html").

---

### Post by yman on 2006-08-09
I added the "less" command, but it came out not that good :(

I emphasized the command names at the begining of each entry as ColdDeath suggested.

I can't use what cleverselfreferentialname had wrote, because I don't have yet internet on my ubuntu laptop and I only have open office on the laptop.

I added a wiki page in the ubuntu wiki because I'm afraid that if I edit this guide myself it would die out like it already is right now. ([link]("https://wiki.ubuntu.com/newbe_to_newbe_guide_to_linux_commands_-_a_documentation_of_a_learning_proccess"))
I don't realy now how to edit a wiki, so it looks horrible.

I discovered the OSS game wesnoth, and I find it to be a superior strategy game to any I have played so far. I spent a whole night and only got through maybe 1/3 of the first campaign. now I'm stuck againsed the men of the plaines. it's realy fun and I especialy like the level in which I return to wesnoth and fight the guards on the border. I had low funds so I used guerilla warfare kicked them to hell and back. no, wait, their dead, so their still in hell. hahahahahaha! :)

---

