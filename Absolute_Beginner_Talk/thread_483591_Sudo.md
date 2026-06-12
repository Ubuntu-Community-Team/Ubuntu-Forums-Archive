---
title: "Sudo"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by arijarot on 2007-06-24
Is there a way to make ubuntu ask for password for every root/sudo task and eliminate the time that the root password is held in memory?

For example, if you open synaptic, then you have entered the root password and it's seems to be stored in memory, in that any other subsequent root task does not prompt you for a password... can this be eliminated?

---

### Post by Happy_Man on 2007-06-24
Oh, you mean the convenient "You just entered the sudo password 30 seconds ago, we'll be nice and not have you enter it again" function. Hmmm..... no, not that I know of.

---

### Post by Pragmatist on 2007-06-24
> **arijarot said:**
> Is there a way to make ubuntu ask for password for every root/sudo task and eliminate the time that the root password is held in memory?

Good question!  The answer is absolutely yes you can.  Read the man pages for sudoers and look for the description of timestamps.  The default is 15 seconds but you can make it whatever you want (including 0).  Here is a quote from the sudoers man page:

> 
 timestamp_timeout
                   Number of minutes that can elapse before sudo will ask for a
                   passwd again.  The default is 15.  Set this to 0 to always prompt for
                   a password.  If set to a value less than 0 the user’s timestamp will 
                   never expire.  This can be used to allow users to create or delete 
                   their own timestamps via sudo -v and sudo -k respectively.


---

### Post by arijarot on 2007-06-25
Thanks, Pragmatist :)

---

### Post by arijarot on 2007-06-25
When I type "time" (and hit "tab" "tab") in the terminal, I only get these options :

time        time-admin  times 

but no timestamp.... how do I add this command?

---

### Post by php_penguin on 2007-06-25
bump this,

i also want to know how to change hte timeout, but i want to go the other way.

---

### Post by Pragmatist on 2007-06-25
Two suggestions:

1.) Modifying the sudoers file can be very dangerous--so dangerous, in fact, that you can't edit it directly!  You must use the visudo comand.  I would strongly advise thoroughly reading about this before doing anything.  If your goal is to improve the security of your system, you would be wise to know what your doing or you can end up accomplishing the opposite.

2.) You can research this very easily using google and the Ubuntu forums.  In less than 5 minutes I found out how to do what you want.  You just use the keywords "sudo" "visudo" "timestamp" in various combinations and you will find what you need.

Normally, I would just give the answer, but in this case I think you should do the research yourself.

---

### Post by php_penguin on 2007-06-25
i have found the visudo manual before your post, but it didn't really help me

furthermore, using the visudo command gave me a file without the timstamp thing in it.

---

### Post by BobCFC on 2007-06-25
[Using sudo tutorial]("http://www.developertutorials.com/tutorials/linux/using-sudo-050511/page1.html")

---

### Post by arijarot on 2007-06-25
so, if this is my sudoers file

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

how/where do I add the line from the [link]("http://www.developertutorials.com/tutorials/linux/using-sudo-050511/page1.html")  

> # Defaults specification

Defaults:jim    timestamp_timeout=0, runaspw, passwd_tries=1 

Can I customize the defaults to

```
Defaults:arijarot timestamp_timeout=0, passwd_tries=2
``` (do I need to include "runaspw"?)

and what does this mean? : ```
Defaults        !lecture,tty_tickets,!fqdn
```

---

### Post by Pragmatist on 2007-06-25
> **arijarot said:**
> 
do I need to include "runaspw"?

From the sudoers man page:
>        
runaspw     
If set, sudo will prompt for the password of the user defined by the
                   runas_default option (defaults to root) instead of the password of
                   the invoking user.  This flag is off by default.

> **arijarot said:**
>  and what does this mean? : ```
Defaults        !lecture,tty_tickets,!fqdn
```
Again, from the sudoers man page:
>  
lecture     
                This option controls when a short lecture will be printed along with the
                 password prompt.  It has the following possible values:
                   never   Never lecture the user.
                   once    Only lecture the user the first time they run sudo.
                   always  Always lecture the user.

                   If no value is specified, a value of once is implied.  Negating the     
                   option results in a value of never being used.  The default value is
                   never.

>       
 tty_tickets 
                  If set, users must authenticate on a per-tty basis.  Normally, sudo
                  uses a directory in the ticket dir with the same name as the user
                  running it.  With this flag enabled, sudo will use a file named for the
                  tty the user is logged in on in that directory.  This flag is off by
                  default.
> 
       fqdn        
Set this flag if you want to put fully qualified hostnames in the sudoers
                   file.  I.e., instead of myhost you would use myhost.mydomain.edu.  You may
                   still use the short form if you wish (and even mix the two).  Beware that
                   turning on fqdn requires sudo to make DNS lookups which may make affect sudo
                   performance if DNS stops working (for example if the machine is not plugged
                   into the network).  The default behavior for Debian has been modified to mini&#8208;
                   mize the potential of a problem, but there may still be some cases in which
                   lack of working DNS might make sudo work very slowly.  Also note that you must
                   use the host&#8217;s official name as DNS knows it.  That is, you may not use a host
                   alias (CNAME entry) due to performance issues and the fact that there is no
                   way to get all aliases from DNS.  If your machine&#8217;s hostname (as returned by
                   the hostname command) is already fully qualified you shouldn&#8217;t need to set
                   fqdn.  This flag is on by default.


---

### Post by BobCFC on 2007-06-25
BTW  I think  !  means not

---

### Post by arijarot on 2007-06-25
Thanks everyone for your help. I got it the way I want it now.

Here it is:

```

sudo cat /etc/sudoers 

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

Password:
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        timestamp_timeout=0,lecture=always,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

Now I'm prompted for the password everytime and given a lecture everytime:)


-----------------------------------------------------
TO php_penguin> 

i also want to know how to change hte timeout, but i want to go the other way.

to achieve this end, according to the [link]("http://www.developertutorials.com/tutorials/linux/using-sudo-050511/page1.html") > If we set timestamp_timeout to -1, "jim" will only have to prove that he knows the password once. After that, it will not be forgotten, even if he logs out. 

so I imagine you'd just add ```
 timestamp_timeout=-1
``` for no timeout or some number >0 for a longer time until timeout...

---

### Post by Pragmatist on 2007-06-25
According to this link: 
[http://www.developertutorials.com/tutorials/linux/using-sudo-050511/page1.html](http://www.developertutorials.com/tutorials/linux/using-sudo-050511/page1.html)
> 
If we set timestamp_timeout to -1, "jim" will only have to prove that he knows the password once. After that, **it will not be forgotten, even if he logs out.**


Perhaps choosing a very large number is the better method.

---

### Post by BobCFC on 2007-06-26
nvm

---

### Post by prkfriryce on 2007-07-27
```

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

Password:
```

Can the above lecture be modified?

---

### Post by Pragmatist on 2007-07-27
> **prkfriryce said:**
> ```

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

Password:
```Can the above lecture be modified?

You want the lecture, but you want to write your own lecture?  Is that right?

---

### Post by prkfriryce on 2007-07-27
> **Pragmatist said:**
> You want the lecture, but you want to write your own lecture?  Is that right?

You are correct.

---

### Post by Pragmatist on 2007-07-27
It is all explained in the sudoers man page:
```
man sudoers
```

You use the string:  [B]lecture_file
[/B]You set the string equal to a path where your alternate lecture file is located. For example:
[B]lecture_file=/home/me/my_lecture_file
[/B]

---

### Post by prkfriryce on 2007-07-27
> **Pragmatist said:**
> It is all explained in the sudoers man page:
```
man sudoers
```

You use the string:  [B]lecture_file
[/B]You set the string equal to a path where your alternate lecture file is located. For example:
[B]lecture_file=/home/me/my_lecture_file
[/B]

just checked my 'man sudoers' :
```

bash-2.05$ man sudoers
No manual entry for sudoers.
```

thanks! :)

---

### Post by Pragmatist on 2007-07-27
I have it on my system, not sure why you do not.  Anyway, there are about a million places online where you can read manpages, here is one:
[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

Here is a google search result page listing many many more:

[http://www.google.com/search?hl=en&q=sudoers+man+page&btnG=Google+Search](http://www.google.com/search?hl=en&q=sudoers+man+page&btnG=Google+Search)

---

### Post by prkfriryce on 2007-08-03
> **Pragmatist said:**
> I have it on my system, not sure why you do not.  Anyway, there are about a million places online where you can read manpages, here is one:
[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

Here is a google search result page listing many many more:

[http://www.google.com/search?hl=en&q=sudoers+man+page&btnG=Google+Search](http://www.google.com/search?hl=en&q=sudoers+man+page&btnG=Google+Search)

yeah, took care of that last week.  Thanks for the heads up

---

