---
title: "Started Ubuntu Today and stuck on GNOME and Internet address!"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by Jennings on 2005-11-30
Hi, I just started using Ubuntu 5.10 today, when I login. it come up with:

"Could not look up internet address for ubuntu.
This will prevent GNOME from operating correctly.
It may be possiable to correct this problem by adding
ubuntu to the file /etc/hosts.
< Log in anyway> < Try again >"

I looked it up on google and came across a couple of things which made no sense to me. Can someone give me a short step by step guide how to fix this?
its really annoying because it dosnt let me use the internet at home (router) or at school (LAN(using the correct port and server Values)), Many thanks in advance

---

### Post by ex` on 2005-11-30
[QUOTE=Jennings]Hi, I just started using Ubuntu 5.10 today, when I login. it come up with:

"Could not look up internet address for ubuntu.
This will prevent GNOME from operating correctly.
It may be possiable to correct this problem by adding
ubuntu to the file /etc/hosts.
< Log in anyway> < Try again >"

I looked it up on google and came across a couple of things which made no sense to me. Can someone give me a short step by step guide how to fix this?
its really annoying because it dosnt let me use the internet at home (router) or at school (LAN(using the correct port and server Values)), Many thanks in advance[/QUOTE]
Are you sure it says "Could not look up internet addres for ubuntu"?
So the host in question being 'ubuntu', and not ubuntu.org?
In any case, the '/etc/hosts'  it refers to is a hosts file comparable with X:\Windows\system32\drivers\etc\hosts, it's a static file containing set domain resolving entries which Ubuntu (and Windows in the case of the X:\windows\... file) queries prior to quering a DNS server.
This allows you to - for example - redirect somewebsite.com to a different computer (IP address) than the one it usually leads to.
The error you described more or less gives away that your computer name under Ubuntu is 'ubuntu', is this correct?
You can check this by running "hostname" in a terminal window (Available under Accesoires -> Terminal).
What the problem seems to be is that the line redirecting your computername to your local IP address does not seem to exist. That is, a static entry of <computername> 127.0.0.1 should exist in order for several programs to work which rely on this 'functionality'.

To solve it, type "sudo gedit /etc/hosts" and insert the following line:
> 127.0.0.1 localhost.localdomain localhost **computername**
'computername' being the value returned by running 'hostname' in the terminal window, in my case it's 'thor', in your case probably 'ubuntu', which will lead to:
> 127.0.0.1 localhost.localdomain localhost ubuntu

Hope this helped. :)

p.s.
If you're not entirely sure of what you're doing, feel free to copy the entire contents of the /etc/hosts file to here and we can see if that's really the problem at hand. :)

---

### Post by Jennings on 2005-11-30
Hi. Many thanks on your swift reply but i am still somewhat confused. I typed in hostname in the terminal and it said ubuntu so i assume that is my comp name. when i type "sudo gedit /etc/hosts", (without the " 's ) it comes up with 

"sudo: unable to lookup ubuntu via gethostbyname()" then comes up with a new line of jennings@ubuntu:~$

please advise. Many thanks on the help so far. the /etc/hosts file just consists of

"127.0.0.1 localhost"

---

### Post by Estariel on 2005-11-30
open a terminal and type the following:
```

echo "127.0.0.1 localhost.localdomain localhost ubuntu" > /etc/hosts

```

this will replace the contents on the file of the right side of the ">" with the contents of the "" on the left side.
If you execute this, it does just what ex` suggested.

---

### Post by Jennings on 2005-11-30
Hi, Thanks but it dosn't work. it come up with "bash: /etc/hosts: permission denied" Is there any other way to change it?

---

### Post by sapo on 2005-11-30
[QUOTE=Jennings]Hi, Thanks but it dosn't work. it come up with "bash: /etc/hosts: permission denied" Is there any other way to change it?[/QUOTE]
he forgot the sudo, type like this:

```
sudo echo "127.0.0.1 localhost.localdomain localhost ubuntu" > /etc/hosts
```

It will ask for your user password, just type it.

---

### Post by Jennings on 2005-11-30
Thanks but it still come up with the same error of "bash: /etc/hosts: permission denied" when put in the terminal. is there something I am doing wrong? I typed it out exactly.

---

### Post by ex` on 2005-11-30
[QUOTE=Jennings]Thanks but it still come up with the same error of "bash: /etc/hosts: permission denied" when put in the terminal. is there something I am doing wrong? I typed it out exactly.[/QUOTE]
Can you do the following then: ls -al /etc/hosts ?
And if it won't work with gedit, you still be able to use nano; "sudo nano /etc/hosts/".
Write the "127.0.0.1 localhost.localdomain localhost ubuntu" line, hit CTRL+X and press 'Y' (to save the changes)

---

### Post by Jennings on 2005-12-01
"ls -al /etc/hosts" brings up 
"-rw-r--r--  1 root root 20 2005-11-30 15:57 /etc/hosts"
and the sudo nano line comes up wuth
"sudo: unable to lookup ubuntu via gethostbyname"
i have a small feeling it might have something to do with not having "admin" on my laptop but there is only one user (myself). is this the case and if so is it changable?

---

### Post by sapo on 2005-12-01
I think you should boot the computer using the ubuntu install cd, than type rescue when it asks for boot option.

It will ask in wich partition is your ubuntu installed, select it.

You will find yourself in a terminal after it boots, then just do:
```
echo "127.0.0.1 localhost.localdomain localhost ubuntu" > /etc/hosts
```

---

### Post by Temis on 2006-01-25
I have the same problem
look at his thread
[http://ubuntuforums.org/showthread.php?t=120420&highlight=log+problem+today](http://ubuntuforums.org/showthread.php?t=120420&highlight=log+problem+today)
Lets see who  will the problem solved first. I will probably reinstalling ubuntu.

---

### Post by gagatz on 2007-01-02
If the ubuntu cd thing didn't do the trick, there is a far easier way:: log in as root, by typing 

su

computer will ask for the password, enter it. You should now be the root@computername. Now typing the same:

gedit /etc/hosts

and inserting the line stated above, should solve the problem. It is now possible again to sudo.

---

