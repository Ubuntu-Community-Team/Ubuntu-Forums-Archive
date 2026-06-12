---
title: "aliasing rm for sudoers"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by chrisg2142 on 2005-12-16
Hi All,

I have been trying to figure out a way to setup an alias for rm, so it will run in interactive mode while I am using sudo.

If I do sudo rm *.txt~ there is no interactivity - all files are deleted.  If I do this same thing without sudo, I do get prompted, but I don't have permissions to delete the file(s).  It is pretty rare that I delete files while using sudo, but I just want to be sure that I don't accidently fat-finger and delete files I don't want to when I do use sudo.

I know there has to be an easy solution, but I am having no luck.  I have tried adding **alias rm='rm -i'** to the */etc/bash.bashrc* file, but I still receive no prompting while using sudo.

I know I can just manually type rm -i (it's only a few additional characters), but I know the one time I don't add the -i, I will delete something I shouldn't have.

I appreciate anyone's help on this.

Chris

---

### Post by darth_vector on 2005-12-16
i *believe* you will have to add the alias to the root users bashrc, rather than your own.

---

### Post by chrisg2142 on 2005-12-17
Thanks for the response darth_vector, however I added **alias rm='rm -i'** to  /root/.bashrc and I am still not getting a confirmation prompt.

So far I have tried adding this alias to the .bashrc file in my home directory, to the bash.bashrc file in the /etc directory, and now the .bashrc file in the /root directory.

Any other thoughts?

---

### Post by GreyFox503 on 2005-12-17
To be more specific:  use this line to edit the root user's bashrc

```
sudo gedit /root/.bashrc
``` 
then append your new alias line.

I forget, but a reboot might be required for the changes to take effect.

EDIT:  Just read your new post.  I've added my own aliases, but never to the root user, only myself.  Did you reboot to test it?

---

### Post by chrisg2142 on 2005-12-17
GreyFox503, I just rebooted, and unfortunately I am still not receiving the confirmation prompt.

Thanks for your assistance.

---

### Post by amohanty on 2005-12-17
gotta test stuff before posting. AFAIK you cannot really set it up that way. Most env vars used during an sudo are the regular users and not the root users. I am not quite sure about the shell but a bit of digging around should get you the answer.

HTH

whoops didnt realise you already saw this. I was wrong about that, posted without testing if the shell is actually used for root. as far I can tell almost nothing other than access rights are transferred unless you create a whole bunch of command aliases in the sudoers file.

edit2: [http://www.courtesan.com/sudo/man/sudoers.html](http://www.courtesan.com/sudo/man/sudoers.html)

---

### Post by chrisg2142 on 2005-12-17
Well this is interesting...

When I do a **sudo alias** I receive the following:
> chris@ubuntu:~$ sudo alias
sudo: alias: command not found


But when I do **alias** without the sudo I get:
> chris@ubuntu:~$ alias
alias cp='cp -i'
alias ls='ls --color=auto'
alias mv='mv -i'
alias rm='rm -i'

---

### Post by GreyFox503 on 2005-12-17
That is weird that sudo alias does that.  I tried it too.

That link that amohanty gave looks good, though I'm not going to test that.

If it doesn't work, you could always make that alias as root, then "su" when you need the privileges.

---

### Post by chrisg2142 on 2005-12-17
I will have to read through the **sudoers** man page and try to make some sense of it.  In the meantime I will "su" as suggested - it does prompt for confirmation (yeah!).

At least I know it wasn't something too simple - so I don't feel like a complete idiot.

Thanks to all who assisted with this.

---

