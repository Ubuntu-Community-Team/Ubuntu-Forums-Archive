---
title: "strategy of user account managment...."
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-11-11
hi 
1)when we say run as root does it mean run with the default account(the first one we set up in the installation)? what about if i create a second account with administrative rights wouldn't that be considered root?

2)i heard it's better not running as a root... ok... that means we have to create accounts  with non administrative rights(specifies by "user and groups" options in administration) but:in this case we cannot run firestarter also because it needs those rights... what can i do?
3)so i thought about applying a king of "strategy":
   -one account for personal/sensitive data(with admin.. rights or not?)
   -one account for downloading with peer2peer,torrents,playing games online,trying some       
     new applications i heard about without being concerned about my other data....
    and the default one first account ...
would that work or it just doesn't really matter?

---

### Post by Ub1476 on 2007-11-11
If you want to you can have on account with personal data, BUT it doesn't require to be admin (root/sudo) for that reason. Root gives you the permission to do everything on your system. with a simply command line with "sudo" in front of it, you can delete your entire partition.

So, if there's an account you want personal data you don't want others to read/see, create an account for that and tell no-one about it.

Your default account works fine for p2p/trying out new apps and so on.

It is not *dangerous* to be admin, unless you really want to screw it yourself (you have to manually write the commands and afterwards write the password to do something "dangerous").

Also, Firestarter isn't really required if you're at home (good to use in public though). Remember Ubuntu already got a built-in firewall. 

More about Root/Sudo here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by scorp123 on 2007-11-11
> **someoneouthere said:**
>  1)when we say run as root does it mean run with the default account(the first one we set up in the installation)? No. It means that you temporarily switch into root's account to execute the function that requires root's infinite God-like priviledges. Most distros will require you to execute "su -" ... On Ubuntu you'd use "sudo", e.g. **sudo /path/to/program/that/needs/root** ....

> **someoneouthere said:**
>   what about if i create a second account with administrative rights wouldn't that be considered root?  No.

> **someoneouthere said:**
>  2)i heard it's better not running as a root...  Especially not "all the time". Root's powers are infinite. If you do something stupid nothing will stop you from doing whatever you are doing. Hence it's better not to use root's powers ... except when they are really really needed.

> **someoneouthere said:**
>  :in this case we cannot run firestarter also because it needs those rights... what can i do?  Use "sudo".

> **someoneouthere said:**
>  3)so i thought about applying a king of "strategy": 
   -one account for personal/sensitive data(with admin.. rights or not?)
   -one account for downloading with peer2peer,torrents,playing games online,trying some       
     new applications i heard about without being concerned about my other data....
    and the default one first account ...
would that work or it just doesn't really matter? You *can* do it of course. I mean UNIX-like operating systems such as Linux were designed to be multi-tasking + multi-user capable (e.g. multiple users can run multiple programs at the same time without getting into each other's way) ... And on servers (e.g. in companies) this is precisely what you do: The programmers need to have access to their compilers, but they have no business messing with the finance application. The database guys can have read access to the system's configuration (they sometimes need to know some parameters) but they should not mess with it. And the finance guys can have their calculator and spreadsheet program of choice and whatever solitaire game they wish, but they sure shouldn't touch the system config, the databases or any of the compilers ...

But for home use? Sounds like overkill. Unless of course you have kids :lolflag:

---

### Post by scorp123 on 2007-11-11
> **Ub1476 said:**
>  Remember Ubuntu already got a built-in firewall.  ... Which does nothing per default. You need programs to define the rulesets if you want the firewall to do something, so you either familiarize yourself with the command line or you use a frontend such as firestarter. Having a firewall in the OS's kernel is one thing, putting it to use so it really does something however is a different story :)

---

### Post by someoneouthere on 2007-11-11
yeah it's sounds a little overkill.... :)

so if i run in terminal with sudo i have root access.. but is there a way "toggle" the root option on/off or check at any time the status?
after some experiments... i realized that admin accounts with no administrative rights cannot use sudo... so no firestarter for them
as for firestarter sometimes i see in blocked/allowed connections "unknown" service or protocol... so firestarter doesn't recocnize  them or he does? (but he does applies policies on them after all)

---

### Post by someoneouthere on 2007-11-11
maybe a good idea idea could be an optional feature for "policy" of the account(or a sub-account)

also something else i heard that in some media filetypes can contain somekind of code inside them that could affect pc.is this also for linux?

---

### Post by magicman5421 on 2007-11-11
by typing sudo before a command you make yourself admin for that session in the terminal. it terminates when you close the terminal window. it is possible to use the root terminal from the applications system menu if you dont want to bother typing in sudo. and what are you talking about admin accounts without administrative rights? isn't an admin account an account with administrator priveleges?

---

### Post by ubnewbie2 on 2007-11-11
> **magicman5421 said:**
> by typing sudo before a command you make yourself admin for that session in the terminal. it terminates when you close the terminal window. it is possible to use the root terminal from the applications system menu if you dont want to bother typing in sudo. and what are you talking about admin accounts without administrative rights? isn't an admin account an account with administrator priveleges?

Actually, typing sudo before a command makes you root for that command ONLY.  You have to put sudo in front of each command.

---

### Post by FuturePilot on 2007-11-11
> **magicman5421 said:**
> by typing sudo before a command you make yourself admin for that session in the terminal. it terminates when you close the terminal window. it is possible to use the root terminal from the applications system menu if you dont want to bother typing in sudo. and what are you talking about admin accounts without administrative rights? isn't an admin account an account with administrator priveleges?
Actually with sudo you're only running that one command as root. Once that command is done executing you are no longer running as root.

---

### Post by someoneouthere on 2007-11-11
the real point is that whatever security you might have if you want to have some fun... you to do it on seperate accounts....

---

### Post by magicman5421 on 2007-11-11
srry forgot about that, i meant that you only have to put in your password once to use sudo in a terminal session

---

### Post by someoneouthere on 2007-11-12
So if i use ktorrent in a limited user account without firestarter just for that i wont have any problems...?

---

