---
title: "Problem with multivolume RAR"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Ev1L on 2007-04-29
I have a big video file splitted with rar.
With windows i can rejoin the packets and sfv tells they're all OK.
When I try to use a GUI, it asks me a password (no password needed, with windows worked), when i try by command line rar e filename.part01.rar it stops at 6th packet for a CRC problem.
I installed rar and unrar in different moment to test separately, but same problem.

Help plz...

---

### Post by paparucino on 2007-04-29
> **Ev1L said:**
> I have a big video file splitted with rar.
With windows i can rejoin the packets and sfv tells they're all OK.
When I try to use a GUI, it asks me a password (no password needed, with windows worked), when i try by command line rar e filename.part01.rar it stops at 6th packet for a CRC problem.
I installed rar and unrar in different moment to test separately, but same problem.

If you downloaded the file via torrent you must ask for a psw to the site from where you got the file.

If the same file was rejoined correctly uner Windows, the same should be under ubuntu.
In a terminal run
```

rar -t filename.rar

```
This test the archive

---

### Post by Ev1L on 2007-04-29
Yes, it comes from torrent, but there's no pass where I took it, and anyway windows extracted perfectly without any passwd.

Of course Ubuntu has to rejoin it too, and I WANT it because I don't want to pray windows everytime I need to rejoin something :)

I tried to test it but I must mistype something because it doesn't work, just lists rar command list like if there would be a syntax error

---

### Post by paparucino on 2007-04-29
> **Ev1L said:**
> Yes, it comes from torrent, but there's no pass where I took it, and anyway windows extracted perfectly without any passwd.
mmmhhhh... may be the psw is required by ubuntu, so try 
```

sudo rar e <filename.rar>

```
if this doesn't work, you must set a root psw this way

```

passwd root

```
answer the questions :-)
then retry the above command


```

Of course Ubuntu has to rejoin it too, and I WANT it because I don't want to pray windows everytime I need to rejoin something :)

```
I had a similar problem, after a few tries I gave it up :-)

> 
I tried to test it but I must mistype something because it doesn't work, just lists rar command list like if there would be a syntax error
you are right I made a mistake. Remove the minus sign in front of t

You can see all parms typing **man rar** in a terminal. They are too much :-)

---

### Post by Ev1L on 2007-04-29
grrrrr...I'll make you two question and let's see if you'll understand what I mean...
1) have you ever tried to take a look to the subtle difference between P and p in bash shell?
2) isn't file splitting in rar and automatic operation that automatically names all the files in the same way?

for who didn't get it, I will explain with another question: why the hell should someone rename some of the files with upper case?!? (or viceversa)

now no more CRC errors or password required with all the files renamed correctly.

thank you for the help anyway

---

