---
title: "root password?"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by irishgoth8822 on 2008-02-08
i just recently had to reinstall ubuntu because it was having some issues, and i forgot how i had originally configured it to not prompt for my root password everytime i tried to start an admin app.

i know i typed something in terminal, and possibly modified a setting under 'users and groups' but i dont remember what i did.

help?

---

### Post by hyper_ch on 2008-02-08
not prompting for root/sudo password is inherently dangerous.

---

### Post by jaytek13 on 2008-02-08
Do you mean permanently, or just you will open up a terminal and type it in once and it won't ask you again after that?

Doing a ```
sudo su
```

will allow you to not have to retype the password in the same open terminal.

---

### Post by irishgoth8822 on 2008-02-08
i mean not prompting for it period. 

for example, when i go to open networking to configure my internet connection, it asks me for a password. i had had it set not to do that, but thats what i cant remember.

---

### Post by PeterJS on 2008-02-08
On second thought, Hyper makes a good point. I hope my attempt as being helpful hasn't caused too much harm.

---

### Post by kellemes on 2008-02-08
Well, you can always use a root-account. ;-)

Edit: removed the howto.

---

### Post by hyper_ch on 2008-02-08
PeterJS:
I don't give out such information. Those who know what they are doing in that state, also know how to get that state or where to find the info on the net. Those do not have to ask in absolut beginners support forums...

---

### Post by dca on 2008-02-08
> **PeterJS said:**
> Like Hyper said running everything with no password is dangerous, please reconsider, but if you must. You're going to want to change this line in your /etc/sudoers file:
```

%admin    ALL =(ALL)  ALL

```
to
```

%admin    ALL = NOPASSWD: ALL

```

NOOO!  You weren't supposed to tell him!!! 
 
Be careful with this...  It's one of the many things that makes posix compliant OSs safer than Windows..

---

### Post by PeterJS on 2008-02-08
> **dca said:**
> NOOO!  You weren't supposed to tell him!!! 
 
Be careful with this...  It's one of the many things that makes posix compliant OSs safer than Windows..

Could you edit your post as well please, I don't want good intentions causing undue harm. I think Hyper makes a good point.

---

### Post by Dr Small on 2008-02-08
> **PeterJS said:**
> Could you edit your post as well please, I don't want good intentions causing undue harm. I think Hyper makes a good point.
How about we just reffer him to the Wiki ;)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2008-02-08
What are people doing so often that password entry annoys them? I rarely make any changes that affect my entire system.

---

### Post by Dr Small on 2008-02-08
> **aysiu said:**
> What are people doing so often that password entry annoys them? I rarely make any changes that affect my entire system.
Some of us like to browse synaptic 10 times a day, and others like to go into users-admin several times a day.... :p

---

### Post by hyper_ch on 2008-02-08
> **Dr Small said:**
> Some of us like to browse synaptic 10 times a day, and others like to go into users-admin several times a day.... :p

And others complain then that their system got hacked...

---

### Post by Dr Small on 2008-02-08
> **hyper_ch said:**
> And others complain then that their system got hacked...
That's generally the way it ends up too, sadly.

---

### Post by bodhi.zazen on 2008-02-08
I say advise someone of the risks, than refer them to the source :

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

IMO, if they want to modify sudo, let them at least read how to and understand what they are doing.

Again, IMO, I do not think we should "spoon feed" users on how to run as root.

Just my 2c :)

In my experience it is often inexperienced uses who want to run as root because, I would imagine, this is easier then learning things like sudo and permissions. After a while though they almost invariably adjust to a new OS and stop running as root, sometimes it is after being cracked or toasting their install, but that too is a learning experience.

---

### Post by jan quark on 2008-02-08
hear, hear
wise words

the knowledge must be free, we are all mature and have our own brains

do not set restrictions

---

### Post by hyper_ch on 2008-02-08
jan:

All the knowledge is out there... one can proof to be ready for it by finding that information himself ;)

---

### Post by jan quark on 2008-02-08
> All the knowledge is out there... one can proof to be ready for it by finding that information himself

whats that a contest ?

who is wiser ?

if someone asks for help I will give him the information he needs.

he does not have to prove oneself worthy, this is not the medieval time :) where advanced ubuntu users dub someone knight


I think evolution works differently, those who learned something new, give this knowledge to the next generation

imagine what would happen when everybody would think like :" yes I know it, but he must find it out on his own"

please this is only my personal opinion and everybody has his own... so peace:lolflag:

---

### Post by kellemes on 2008-02-08
> **jan quark said:**
> 
I think evolution works differently, those who learned something new, give this knowledge to the next generation


You're not alone in thinking this ;-)

As long as you explain the risks there is nothing wrong with answering the question.. actually it's rather silly to purposely withhold information to "protect" someone.

But hey, luckily Google isn't restricting at all. ;-)

---

### Post by hyper_ch on 2008-02-08
> **kellemes said:**
> As long as you explain the risks there is nothing wrong with answering the question.. actually it's rather silly to purposely withhold information to "protect" someone.
Would you hand a child a loaded gun and explaining how dangerous it is?

> **kellemes said:**
> But hey, luckily Google isn't restricting at all. ;-)
You're wrong on that... google is also restricting ;)

---

### Post by jan quark on 2008-02-08
we are not children

we understand the meaning of the written words

I can't say anything to restrictions in google 
do not have the needed background and proofs

---

### Post by hyper_ch on 2008-02-08
> **jan quark said:**
> we are not children

we understand the meaning of the written words

I can't say anything to restrictions in google 
do not have the needed background and proofs

Google censors in certain countries ;) so there are restrictions in google...

Well, you may not be children in your biology but you maybe children in the usage of POSIX systems ;)

> **jan quark said:**
> we understand the meaning of the written words
Not when it's about computers as it occurs to me ;)

---

### Post by jan quark on 2008-02-08
hyper_ch

it is a pleasure to discuss with you but we are a little bit off topic now, don't you think? :)
let us focus on the crucial part of our "job" here again.

ceasefire? :)

---

### Post by irishgoth8822 on 2008-02-09
i think maybe ya'll misunderstood what i want to do. all i want to do is make it so that when i login when ubuntu first boots, on the main login screen where it prompts for username and password, it will sign me as root so i dont have to put in passwords when im logged in under my main username.

---

### Post by y-lee on 2008-02-09
> **irishgoth8822 said:**
> i think maybe ya'll misunderstood what i want to do. all i want to do is make it so that when i login when ubuntu first boots, on the main login screen where it prompts for username and password, it will sign me as root so i dont have to put in passwords when im logged in under my main username.

No everybody understands what you want. the point being:

 **[SIZE="3"]It is a very very terrible idea to sign in as root !!.[/SIZE]**

If you do so you lose almost  all the security advantages of having a unix/linux type operating system. you may as well be running windows in admin mode which is windows default (until vista that is). Even microsoft has taken to having security precautions much like Linux with Vista, which is a good thing unfortunately Vista suxs for other reasons imho.

If you sign in as Root you can very easily destroy your system, you are vulnerable to attack from the outside (ie black hat hackers) you are vulnerable to what ever few linux viruses and spyware that actually exist, and programs you install might have priviliges they DO NOT need and SHOULD NOT have and even they could hurt your system should they malfunction.

All in all if you sign in as root alot chances are nearly 100% you would trash your system.

I have no problem helping people here and I do not beleive in censoring ideas but I am not going to help ya trash your system because I might end up being the one to help ya fix it. :lolflag:

---

### Post by irishgoth8822 on 2008-02-09
well, alright. the reason im so insistent on asking is because the last time i had it set up as this much-safer-default, i had this problem:

[http://ubuntuforums.org/showthread.php?t=460108](http://ubuntuforums.org/showthread.php?t=460108)

---

### Post by amingv on 2008-02-09
> **irishgoth8822 said:**
> well, alright. the reason im so insistent on asking is because the last time i had it set up as this much-safer-default, i had this problem:

[http://ubuntuforums.org/showthread.php?t=460108](http://ubuntuforums.org/showthread.php?t=460108)

I see no reason for that to happen again...

I think 3 pages telling you not to are quite enough. Reminds me of my grandfather and his smoking habit (nice guy, sadly is dead now, he's missed).
I couldn't stop him from smoking, but I wouldn't have gone to the grocery store and buy cigarettes for him if he begged me.

The answer to your question is one google search away, a very simple one-line command, but we do not want to give it on the hope that you'll reconsider. Please understand.

---

