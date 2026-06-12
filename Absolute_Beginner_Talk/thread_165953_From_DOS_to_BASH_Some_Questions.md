---
title: "From DOS to BASH: Some Questions"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by charlie. on 2006-04-25
I have spent a large amount of time using the Bourne Again SHell and I have become quite familiar with it. The more I use it, however, the more things I discover that I don't know. There are many techniques that I know well from DOS, but can't quite work out the BASH equivalent for. Here are some that I encountered today...

[LIST=1]
[*]In DOS, if you type in a command and decide to abort the command, you can press ESC to clear the prompt so that you can start again. This is quite usefull if you are scrolling through your history and can't find the command you are looking for or you change your mind half way through. How do you do this in BASH?
[*]I have noticed a few applications, like Pico, sometimes exit with the cursor in the middle of the screen, lost in the midst of the wreckage of previous commands and output. In DOS, CLS will clear the screen and give you a cursor at the top, easily visible. How do you do this in BASH?
[*]In DOS, I use ipconfig frequently to check the IP address or MAC address or release and renew the data that I have acquired from DHCP. This is usefull if I change settings on my DHCP server, such as the list of DNS records or gateway, and I want to test the changes. I know that ifconfig will give me the IP and MAC addresses in linux, but I cannot work out how to release and refresh the DCHP address or get DNS/gateway addresses from ifconfig. How do I do this?
[/LIST]

Thanks for all the help. As each question is answered, I become more at home in the Bourne Again SHell. That is a good thing!

---

### Post by tsumi on 2006-04-25
1. crtl + c

2. "clear"

3. "ifconfig"

---

### Post by mjm115 on 2006-04-25
[QUOTE=charlie.]

In DOS, if you type in a command and decide to abort the command, you can press ESC to clear the prompt so that you can start again. This is quite usefull if you are scrolling through your history and can't find the command you are looking for or you change your mind half way through. How do you do this in BASH?[/quote]

The ESC key should work just fine in bash as well, or CTRL+C

> 
I have noticed a few applications, like Pico, sometimes exit with the cursor in the middle of the screen, lost in the midst of the wreckage of previous commands and output. In DOS, CLS will clear the screen and give you a cursor at the top, easily visible. How do you do this in BASH?

Try typing the 'clear' command

> 
In DOS, I use ipconfig frequently to check the IP address or MAC address or release and renew the data that I have acquired from DHCP. This is usefull if I change settings on my DHCP server, such as the list of DNS records or gateway, and I want to test the changes. I know that ifconfig will give me the IP and MAC addresses in linux, but I cannot work out how to release and refresh the DCHP address or get DNS/gateway addresses from ifconfig. How do I do this?

sudo dhcpcd -k eth0

---

### Post by mlind on 2006-04-25
1. ctrl-c
2. ctrl-l
3. sudo dhclient eth0

---

### Post by joshrobinson on 2006-04-25
if you are used to typing DOS commands all day such as copy move rename del deltree etc etc. you can also create aliases for your commands such as

alias (dos command)='(linux command)'

example:

alias del='rm'
alias copy='cp'

i know you werent asking about this, but i thought you might appreciate it

---

### Post by echo $USER on 2006-04-25
[QUOTE=joshrobinson]if you are used to typing DOS commands all day such as copy move rename del deltree etc etc. you can also create aliases for your commands such as

alias (dos command)='(linux command)'

example:

alias del='rm'
alias copy='cp'

i know you werent asking about this, but i thought you might appreciate it[/QUOTE]

Are alias stored perminenlty or just for the current session?  And if they only last for the current session how would I export them so they are perminent?

---

### Post by Randomskk on 2006-04-25
Add the alias command to you .bashrc file in your home directory, I believe, to make them last.

---

### Post by htinn on 2006-04-25
If find yourself discovering other differences, you might keep in mind this one:

```
help
```

That gives you a list of commands and a brief syntax.

---

### Post by charlie. on 2006-04-26
Thanks,

**Ctrl+C** aborts the current line perfectly.
**Ctrl+L** clears the screen. ('clear' works too)

I could not get any usefull information from dhclient or dhcpd, however.

---

### Post by mlind on 2006-04-26
[QUOTE=charlie.]Thanks,

**Ctrl+C** aborts the current line perfectly.
**Ctrl+L** clears the screen. ('clear' works too)

I could not get any usefull information from dhclient or dhcpd, however.[/QUOTE]

*man dhclient* should show manual entry for this program.
sometimes /sbin/ path is not on your $PATH variable entry, like in Fedora, 
but Ubuntu should include /sbin/ by default.

to find out this, try
```

whereis dhclient
echo $PATH

```

---

