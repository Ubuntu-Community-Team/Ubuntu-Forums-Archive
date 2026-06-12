---
title: "Password for root user in Live CD =&gt; install"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by kOracle on 2007-06-26
Hi all,



I just now started trying ubuntu with the cd i got from the ubuntu ppl.


in the live cd there was a install icon to install the OS in my system, so clicked that and installed it in my VmWare virtual machine.... cool all went fine and no big things.... the problem came soon with the OS startup.....  when i apt-get the lex since it din came with the CD ...... ROOT password..!!!!!!!! damn it din asked me for setting the root password during the installation.....

so i assume that the root password for the Live Cd should still be the root password after installation also....
can anyone u please pass me the root password pls..... [correct me if i were wrong somewhere]

thnx in advance

---

### Post by cogadh on 2007-06-26
Its asking for your password, not root's. Ubuntu doesn't really use the root account, it assigns temporary superuser access through the sudo command, which requires you own password. When you use apt, the commands should be entered like this:
```
sudo apt-get install packagename
```

---

### Post by bodhi.zazen on 2007-06-26
> **kOracle said:**
> Hi all,



I just now started trying ubuntu with the cd i got from the ubuntu ppl.


in the live cd there was a install icon to install the OS in my system, so clicked that and installed it in my VmWare virtual machine.... cool all went fine and no big things.... the problem came soon with the OS startup.....  when i apt-get the lex since it din came with the CD ...... ROOT password..!!!!!!!! damn it din asked me for setting the root password during the installation.....

so i assume that the root password for the Live Cd should still be the root password after installation also....
can anyone u please pass me the root password pls..... [correct me if i were wrong somewhere]

thnx in advance

On the live CD there is no root password.

In a terminal enter :

sudo -i
sudo -s
sudo su

for commands just use sudo 

sudo <command>

while on the live CD you will not be asked a password.

HD install, use your log-in password.

---

### Post by kOracle on 2007-06-26
ohh okie okie got it.... 

linux#man sudo_root           //"""""""damn i should have read the first line in the terminal !!!!!!!!"""




 then since there will be no root wont it make my system vulnerable for attacks,.....

since i am browsing like a root user ????


i din see any thing like this in my previous linux [ openSuSE]..... where it clearly seperates the normal users from the root user

---

### Post by bodhi.zazen on 2007-06-26
Yes, but not exactly ...

The live CD is different from the behavior of a HD install. The live cd uses a user "ubuntu" who is not root.

"ubuntu" has root access via sudo, but sudo is configured so as not to require a password.

After you install to HD the situation is similar. The first user is automatically a member of the admin group (others are not, although they can be added). On a HD install you still access root via sudo, but now a password is required (your log in password).

The root account is locked so you can not log in as root or su.

You can :[list][*]enable the root account by giving it a password[*]sudo su ; sudo -i ; sudo -s[/list]

You configure sudo with visudo

You can configure it such that no password is required, but folks do not do that ....

See these links :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://sudo.rtin.bz/sudo/man/sudo.html](http://sudo.rtin.bz/sudo/man/sudo.html)

[http://sudo.rtin.bz/sudo/man/sudoers.html](http://sudo.rtin.bz/sudo/man/sudoers.html)

That last link ^^ is a more detailed description of how to configure sudo ;)

Is it better ? Better is soooo relative :)

---

### Post by cogadh on 2007-06-26
You are not using a root user, you are using a normal user. The sudo command just gives you root privileges for the command it used on. If you try running another command that requires root access without using sudo, it won't work. Honestly it is really no less safe than using the root account as is done in other distros, you just need to protect your own password as if it were a root password.

EDIT - Damn! bodhi types fast!

---

### Post by rillip on 2007-06-26
Also keep in mind that the LiveCD isn't intended to be as secure, robust, etc. as a full install.  There have to be some compromises in this regard.

Just on a side note, does anywhere here know right off hand what runlevel the LiveCD boots to? I imagine runlevel 3, which means the security is increased that much more when you boot from your HD install, since it's running in level 5.

---

