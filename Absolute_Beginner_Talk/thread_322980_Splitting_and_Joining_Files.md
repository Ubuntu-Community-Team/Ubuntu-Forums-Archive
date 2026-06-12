---
title: "Splitting and Joining Files"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by namaku.syntia on 2006-12-21
Hi,

I'm trying to find a programme that acts like "The File splitter" in M$, but can't find a single one that has Graphical User Interface.

So, I used split (from console).
> >>split --bytes=200m input_file
the input_file's size is about 300MB. i got 2 files as result, file 'xaa' and file 'xab'.

Then I tried to join those 2 files, using join (from console)
> >>join xaa xab
i thought it worked because i need to wait for several minutes, like the splitting process.
but after the process finished, i can't find the output anywhere. :confused: 

is there something wrong with the command that i used?

i really need the result urgently..

thank you in advance.

regards,
Syntia Wijaya

---

### Post by kidders on 2006-12-21
Hi there,

"join" is **not** the reverse of "split". (See join's man page for info.)

If it were me, I'd try stringing multiple files together with something like **cat chunk* > whole**, although I'd be a bit nervous that the various chunks might not necessarily get put back together in the right order.

Give it a try and see what happens. If something goes pear-shaped, you could try explicitly sorting your file chunks first, with something like **for i in $(ls chunk*|sort); do cat $i >> result; done**

There might be a smarter way of doing this, but nothing comes to mind.

---

### Post by namaku.syntia on 2006-12-21
Hi,

I thought "cat" can only be used for text files. The original file that I splitted is .avi file.

I used "cat" and sort the files manually.
> >>cat xaa xab >result.avi

and it works flawlessly..

Thanks alot.. :D

---

### Post by TooRight on 2006-12-21
What kind of file is it? For .avi movies I use avimerge at the command line. To get it,  

> 
sudo apt-get install avimerge


and then to use it, just

> 
 avimerge -o filename_you_want_it_to_be.avi -i first_file.avi second_file.avi


I know it's not a graphical one, but seriously, it's sooo simple and sooo fast!! 


Hmmm...wait a minute, I think avimerge is already installed automatically, lol, so just skip to the second step

For the "first_file.avi" and second_file.avi, I just open up the directory where they are located (in konqueror), and then drag the file into the terminal window...it gives it the correct paths etc.

---

### Post by namaku.syntia on 2006-12-21
i

---

### Post by namaku.syntia on 2006-12-21
Hi TooRight, thanks for the reply..

I'd like to try the avimerge programme but it seems that i can't find the programme in the repository i used [http://kambing.vlsm.org](http://kambing.vlsm.org). Well, it's the most complete repository in Indonesia.

So I changed the file /etc/apt/sources.list into:
> deb [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) dapper main restricted multiverse universe

but still, I got the "couldn't find package" error.

Anyway, can "avimerge" merge files that are splitted by "split"? I mean, does it work sequentially (adding the second file right behind the first file)? Besides, I think the second file that results from "split" is not .avi file, since I failed to open it using mplayer. The first file can be watched using mplayer. 

Thank you..

regards,
Syntia Wijaya

---

### Post by jackthecoiner on 2007-11-10
The avimerge binary was installed on my system when I added the package "dvd::rip".  Additionally, avifix, aviindex, avisplit, and avisync were also added.

I'm not sure about your question re: interoperability with the "split" binary, but avimerge certainly works as expected with avisplit.

---

