---
title: "Copy files from one folder to another"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by barrykgerdes on 2007-02-23
I would like to copy or move files from one folder to another using the terminal.

It is easy in the GUI but I don't know the command line terms.

Barry

---

### Post by Maestro23 on 2007-02-23
> **barrykgerdes said:**
> I would like to copy or move files from one folder to another using the terminal.

It is easy in the GUI but I don't know the command line terms.

Barry

> cp file1.txt newdir (copies file1.txt to directory newdir).

cp *.txt newdir (copies all .txt files to directory newdir)



*In a terminal you can type for any command, (Ex. man cp)

> man cp

*Will give the syntax for the cp command.

Many options with the copy command.  Links below will discuss as well.

copy command: [http://www.computerhope.com/unix/ucp.htm](http://www.computerhope.com/unix/ucp.htm)
CommandLine Beginner's: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

---

### Post by Kateikyoushi on 2007-02-23
These are the basic terminal commands. [LINK]("http://www.linux.org.mt/node/49#N1029D")

you can use cp path/to/file1 path/to/where you want to copy it. In case you are in the directory where the file is the path is not necessary.

---

