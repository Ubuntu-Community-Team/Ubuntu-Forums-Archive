---
title: "Manual (manpage) sections"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by msandersen on 2006-09-05
In documentation referring to manpages (specifically other manpage entries), they use the form "programname(number)" as in man *program* section [*number*].
However, if I go **man man** to find out how to go to a section, it doesn't actually tell you how to use this information, which is pretty stupid, or else it is buried in the technical jargon.
So, how do you go to a specific manpage section?

---

### Post by meng on 2006-09-06
man [section number] [program name]
e.g.
man 1 man
man 8 ping

---

### Post by LadyDoor on 2006-09-06
I think what you're talking about is the part of the manpages that looks like this (example taken from the mutt mailreader's manual).

```

SEE ALSO
       curses(3), flea(1), mailcap(5), maildir(5), mbox(5), mutt_dotlock(1), muttrc(5), ncurses(3), sendmail(1), smail(1)

```

The number after it tells you what type of file/application/etc. the man page referenced documents. For example, doing **man curses** would bring up the man page on curses, which is "type 3." It's not referring you to a section of the manual you're looking at. I hope that helps!

--Door

---

### Post by bodhi.zazen on 2006-09-06
> **msandersen said:**
> In documentation referring to manpages (specifically other manpage entries), they use the form "programname(number)" as in man *program* section [*number*].
However, if I go **man man** to find out how to go to a section, it doesn't actually tell you how to use this information, which is pretty stupid, or else it is buried in the technical jargon.
So, how do you go to a specific manpage section?

Nice question.

---

### Post by msandersen on 2006-09-06
> **LadyDoor said:**
> I think what you're talking about is the part of the manpages that looks like this (example taken from the mutt mailreader's manual).

```

SEE ALSO
       curses(3), flea(1), mailcap(5), maildir(5), mbox(5), mutt_dotlock(1), muttrc(5), ncurses(3), sendmail(1), smail(1)

```

The number after it tells you what type of file/application/etc. the man page referenced documents. For example, doing **man curses** would bring up the man page on curses, which is "type 3." It's not referring you to a section of the manual you're looking at. I hope that helps!

--Door
So what's the "type"? Why is the number listed in the references? If I go **man samba** it says at the top **samba(7)** and the various sub-programs have their own "type", eg **smbclient(1)** or **smbpasswd(8)**
If I go **man 8 samba** (nonexistant)
it says
**No manual entry for samba in section 8**
so it refers to a section.

It must be listed for some reason. I though it might have been like an anchor in HTML, jumping to a specific part of the manpage, or even a separate detail page, like with infopages.

---

### Post by LadyDoor on 2006-09-06
> So what's the "type"? Why is the number listed in the references?

To quote from the **man** manual (**man man**),

```

       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions eg /etc/passwd
       6   Games
       7   Miscellaneous  (including  macro  packages and conven&#8208;
           tions), e.g. man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]

```

> If I go man samba it says at the top samba(7) and the various sub-programs have their own "type", eg smbclient(1) or smbpasswd(8)

Yeah, this tells you which type each manpage is.

> If I go man 8 samba (nonexistant)
it says
No manual entry for samba in section 8
so it refers to a section.

This is because samba is type 7, as you can note in its man page. Therefore, you could also type **man 7 samba** and have it come up. Similarly, to view the smbpasswd man page, you could type **man 8 smbpasswd** or more simply **man smbpasswd**--it's a different man page.

> It must be listed for some reason. I though it might have been like an anchor in HTML, jumping to a specific part of the manpage, or even a separate detail page, like with infopages.

It's listed to tell you which of the directories in **/usr/share/man** the manual page is located in. In addition, some man pages have identical names--such as **man(1)** and **man(7)**. So the default when you type **man man** is to send you to man(1). But what if you want to read about the macros used to format man pages? That's when you need the number. You would type **man 7 man** to view that page. And manpages don't work like HTML or info...sorry.

If you're still confused or want more info, please feel free to either ask here or to read the man(1) manpage (**man man**).

I hope that helps,
Door

---

### Post by msandersen on 2006-09-06
Thanks.

---

