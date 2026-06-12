---
title: "How to install *.run packages"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by feap on 2006-10-22
I downloaded Wolfenstein and True Combat: Elite and they are both *.run packages. I've googled and looked here but there's no installation instruction for .run files. How do I install?

I tried with sh ./foo.run which worked until the Wolfenstein installation program asked for a path. The default path was /usr/local/games/enemy-territory but I got "no permission to write" error.

Also, how do I install the TC:E package as it's a Wolfenstein mod? Other instructions here and elsewhere are for the .zip version of the installation package.

---

### Post by Esben Kramer on 2006-10-22
Type sudo before the sh ./foo.run command : sudo sh ./foo.run

This should give you write-priveliges.

---

### Post by mostwanted on 2006-10-22
[http://monkeyblog.org/ubuntu/installing/#permissions](http://monkeyblog.org/ubuntu/installing/#permissions)

---

### Post by feap on 2006-10-22
I got it installed with sudo, thx! Then it took only about an hour to get True Combat: Elite installed since I needed to figure out how to copy stuff to /usr/... dir, and then how to give write permissions to the punkbuster dir. Why is everything so hard in Ubuntu?

---

### Post by nickpaton on 2006-10-22
Running a brand new install of Edgy.

Also downloaded Wolfenstein into /home/nick folder, which currently resides as a 256Mb .run Shell Script.

From home/nick, as instructed, ran sudo sh ./foo.run (cant obviously move to the wolfenstein file since it's not a folder.)

Running the above command in a Terminal I get following error message:

sh: Can't open ./foo.run

What am I doing wrong?

Also don't see any specific help in [http://monkeyblog.org/ubuntu/installing/#permissions]("http://monkeyblog.org/ubuntu/installing/#permissions")

as suggested by mostwanted (but useful link anyway - Tks!)

---

### Post by moffa on 2006-10-22
It's not that it is hard, it is just that is it more secure than Windows.  Sure you can login and run everything as root but highly recommended that you do _not_ do that.

You've got to remember it is a completely different OS.  Once you get used to it, you'll realize how good it is.

---

### Post by nickpaton on 2006-10-22
Worked it out

'et-linux-2.60.x86.run' is the Wolfenstein download

Sort out permissions:

```
chmod +x et-linux-2.60.x86.run
```

Install the program:

```
sh ./*.run
```

I'm not sure what 'foo' is or what it's got to do with installing .run programs - would greatly appreciate it if someone could explain foo to me.

Many thanks all!

---

### Post by po0f on 2006-10-22
nickpaton,

[Foo](http://en.wikipedia.org/wiki/Metasyntactic_variable).

[Foo](http://www.urbandictionary.com/define.php?term=foo).

[Foo](http://catb.org/jargon/html/F/foo.html).

---

### Post by nickpaton on 2006-10-23
> **po0f said:**
> nickpaton,

[Foo](http://en.wikipedia.org/wiki/Metasyntactic_variable).

[Foo](http://www.urbandictionary.com/define.php?term=foo).

[Foo](http://catb.org/jargon/html/F/foo.html).

Thanks

Thanks

and err.....

Thanks!!!:D

---

