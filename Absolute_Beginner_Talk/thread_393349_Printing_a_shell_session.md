---
title: "Printing a shell session"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by goatboy78 on 2007-03-25
Hello fellows

I am VERY new to Linux and I was wondering if anyone could help me with something.

Is there a simple command that will grab the contents of a terminal window and send it to a printer? If so, what is it?

Also, I would me interested in any similar command that would send the information to a file.

Thanks

Goatboy

---

### Post by Tadhg on 2007-03-25
for sending info to a file you can use indirection using the ">" operator. So if you want to write the contents of a directory to a file, type

for the printer thing, you could use the "|" operator, which pipes the info from the first command to the command after the pipe, that being whatever the terminal print command is (I've never printed using terminal)

$ ls > nameoffile.txt

read up [here]("http://www.cpqlinux.com/redirect.html")

---

### Post by goatboy78 on 2007-03-25
Thanks for that

---

### Post by goatboy78 on 2007-03-25
Does anyone know the terminal print command?

---

### Post by Kamu on 2007-03-25
If you mean how to tell the computer to print a file from the command line, the command is normally lpr.  To get the complete description type: man lpr

Typical use is:
lpr -Pprinter_name   file_name
no space between -P and the name of the printer

---

### Post by goatboy78 on 2007-03-26
This is all good stuff, but not quite what I mean.

Lets just say that I've run a few commands in a terminal that have generated quite a lot of textual output. I want to study that output later.

I could copy and paste it all into a text file and then print it out, but is there a command that will do that for me, i.e send the text from the terminal window to a file or a printer?

---

### Post by Kamu on 2007-03-26
Alright, then the information you got from Tadhg is what you need, but maybe I can try to rephrase it so it's a bit more detailed.

if for example I use the command "ls" to list the content of a directory:
kamu@kamu-box$ ls
file1.txt
file2.txt
file3.txt

if I use the operator >, I can get the output of ls into a new text file.
kamu@kamu-box$ ls >filelist.txt
which you can read back
kamu@kamu-box$ cat filelist.txt
file1.txt
file2.txt
file3.txt
also, the braindead way to merge some of these text files in one big one for printing is:
kamu@kamu-box$cat filelist1.txt filelist2.txt filelist3.txt >full_filelist.txt

when if you look at the full_filelist.txt contents, it will be in order the contents of the files listed as arguments of "cat".

It's a bit of a brute force way to go about things, but it has the advantage to be very simple.

---

### Post by goatboy78 on 2007-03-26
Yeah, I'm aware of this type of command and I use it quite a lot. However, it is only useful if you know in advance that you will want to print the output of a command.

What I want to know is how to print out the output retrospectively, when it is already sitting in the terminal window.

To use your example, if I were to type ls to list the contents of a directory, is there a command that I can then invoke to print the output.

I realise that in the context of this example, such a command would be unnecessary, but some commands generate a lot of output that you don't always know about in advance.

---

### Post by Kamu on 2007-03-26
Ah, ok.  I'm sorry, I misunderstood what you were trying to do.

I usually use the KDE Konsole for my terminal.  For Konsole, I can go to Edit->SaveHistoryAs... and save the last lines printed to the screen, up to the number of lines set in Settings->History...

The terminal command "history" will return the command history, but not the output from those commands.  It's not very consistent behaviour but that's how it is.  If you are using another terminal, I'm afraid I don't know anything else that can help you, sorry.

---

### Post by annda on 2007-03-26
i'm not sure you can print the contents of the whole console buffer - i think it's just stored in memory. as i understand it, command output is sent to, well, standard output - being the console window. it is not written anywhere, so you can't access it.

however, you can easily print the outputs of previous commands using the bash history and info from the above posts.

using the UP and DOWN arrows, select the command whose output you want to print and use the pipe to redirect the output to lpr, which manages your printing queues, e.g.

ls -al | lpr

if you have no standard printer, or lpr is confused, specify the printer name with -P

ls -al | lpr -Pprinter_name

since many of us do not use parallel printers anymore (so lp is no longer the standard queue), find out the name like that (it's before the pipe):

cat /etc/printcap

you can set the PRINTER variable in your .bash_profile or .bashrc for future use.

---

### Post by goatboy78 on 2007-03-26
Thanks fellows

That is a big help.

Regards

Goatboy

---

### Post by peterquistgard on 2007-12-18
I find the "script" command really useful for saving shell input / output.

To use it just type "script" at the command line before you start. When you're done, type "exit" at the command line, This will save everything that appeared in the terminal to a file called "typescript".

You can specify a different output file if you want to. Just type "man script" at the command line for more information.
:guitar:

---

