---
title: "[SOLVED] sudo/root/permissions issues"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Canew on 2008-01-23
Hi:

I've seen some answers to these questions in other threads, but I'm still not sure I entirely get it. I'm in a weird place now where I'm knowledgeable in some areas of Ubuntu, and clueless in others, so bear with me if any of these questions have been seen/answered before.

I have taken the advice of many and created a shell account (called, oddly enough, Canew) which I use instead of root for the majority of my computing. Of course, I don't get that "software updates available" blurb that pops up when I log in as root, I can't modify some system settings and I can't use the installation manager (forget the name off the top of my head) to browse and/or install programs (before anyone says it, I don't want to use sudo apt-get. I'm a Windoze transplant. I like the GUI. Sue me.), so I need to jump on as root from time to time.

My first question: Sometimes, when I'm installing updates, performing system maintenance, tweaking settings, or installing/removing programs, a box pops up asking for my root password. Erm, hello? I'm LOGGED IN AS ROOT. Why do I need to give it my password AGAIN?

Next, another time, while running into problems getting a playlist to work in Rythmbox, I decided to log in as root and use the same application to get it to work, which meant I had to copy/pull it out of my shell directory into root. It tells me I don't have permission. Permission? Helloooo... I'm LOGGED IN AS ROOT. I thought that was the "superuser." I thought root needed no "permission" to do anything. Am I wrong?

Regarding sudo, I think I've had to use sudo a couple times while logged in as root to do something in terminal. Why would I even need this? I'm root. That's all the system needs to know, right? Further, why is it using sudo in my shell account doesn't work? I'm using the root password. Isn't that how to access superuser privileges?

---

### Post by rbc on 2008-01-23
Things may have changed since I first installed Ubuntu, so don't take this as gospel, but the way I understand it.....unlike most GNU Linux distros, Ubuntu does not have a root login. By default, the first user created is an "administrator", as opposed to a normal user with fewer privileges. When you use the Synaptic Package Manager or do any other administrative task, the password you're typing is the password for that Administrator, not root. Then again, I may have totally misunderstood your question and/or be completely wrong

---

### Post by meindian523 on 2008-01-23
rbc is correct.There's no GUI login for root in Ubuntu.What you are referring to as root is actually the normal user account+some privileges.

what you have actually done gone is mistaken the normal user+admin privileges account for the ultra-god account and created a normal user-admin privileges account for yourself,got it?You can safely use the normal user+admin privileges account for daily computing since anytime you do something to do with admin,you will be asked for your password.

---

### Post by dstew on 2008-01-23
How did you enable the root account?

---

### Post by Canew on 2008-01-23
So there is no root login anymore? I tried using Red Hat a loooong time ago (seems it anyway), and I recall being practically shrieked at in the forums that I should NOT use the default account, that this is the root directory and if something got screwed up there was no way to fix it, blah blah, and that I simply HAD TO HAVE a shell account, and use that account to store all files, do all day-to-day, non-administrative stuff, etc.

So Ubuntu works differently? No root superuser login? Sorry to sound so cluless, but this is a totally new idea to me.

EDIT: to log in as root, I use the "first user" created, which I happened to name "gonzo." If I log in as gonzo, I get access to Synaptic, system settings, etc. I thought this was the superuser. I guess not?

---

### Post by meindian523 on 2008-01-23
dstew,he didn't.He mistook the normal account for root.

---

### Post by meindian523 on 2008-01-23
> **Canew said:**
> So there is no root login anymore? I tried using Red Hat a loooong time ago (seems it anyway), and I recall being practically shrieked at in the forums that I should NOT use the default account, that this is the root directory and if something got screwed up there was no way to fix it, blah blah, and that I simply HAD TO HAVE a shell account, and use that account to store all files, do all day-to-day, non-administrative stuff, etc.

So Ubuntu works differently? No root superuser login? Sorry to sound so cluless, but this is a totally new idea to me.

There IS a root account,only that GUI login is disabled by default.You can login in CLI using sudo -i and inputting your password,got it?Of course,the above applies only to normal user+ admin privileges account,or any other account which belongs to the admin group.

---

### Post by meindian523 on 2008-01-23
yes,that's correct,gonzo is the normal+admin account,NOT the superuser.

---

### Post by Canew on 2008-01-23
Ok, I think I'm getting this. So my "first account," i.e. Gonzo, is NOT a superuser, just a "main user." This explains a lot. It just so happens, however, that it has the same password as root, which is further confusing me. Are you saying I could change Gonzo's password and still use the "old" password as the root password?

Figures. I finally figure out the ins and outs of root/shell accounts, and I come across a Linux distro that works differently. Just my luck. :(

---

### Post by meindian523 on 2008-01-23
One more difference:
The root login in Ubuntu has a login id root and NO PASSWORD!You have to set the root password by using your gonzo account if you want that root should have a password.If you change Gonzo's password,you will have to use the NEW password for all admin tasks including sudo,etc.

What this leads to is that Gonzo's password and root password have NO interrelation.

---

### Post by monte48lowes on 2008-01-23
Being a windows user the method used by ubuntu should be familiar. The first account created is setup as an 'administrator' account. Very similar to winXP. 

Mike

---

### Post by philinux on 2008-01-23
The first acount created is similar to a limited user but with access to administrator rights by the use of the sudo command via terminal or in a gui like synaptic.


For the OP
[http://www.psychocats.net/ubuntu/security#sudomoreinfo](http://www.psychocats.net/ubuntu/security#sudomoreinfo)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by meindian523 on 2008-01-23
Thanks Phil for those links.

---

### Post by Canew on 2008-01-23
Thanks for the info, all. Those links are informative.

Re: Windows XP. My gf's computer has it, but she doesn't "log in," so I'm not familiar with that concept. I've never had XP on one of my computers. Last Windoze environment I had (about a year ago) was Windows 98 SE. Yep, it was time for an upgrade, and I had had it with Windoze. I love Ubuntu, and as I said, I've learned a lot, but some things I'm still foggy on.

Ok, so it is possible to log in as root by typing "root" as the username, and using a password I set as administrator (Gonzo), right?

Course, if the admin can do almost anything, there seems to be no reason to log in as root, is there? Must be why the admin user is there in the first place (the light dawns!)

Bear with me, guys. I'm learning. :)

---

### Post by philinux on 2008-01-23
The best practise is to login as the "limited user" if you will. The first user acount is always a member of the group admin. This way when you run firefox on the internet you're much safer. Anything nasty would have to have the root password, your password to install anything. 
If you run your system as root, like win98 or XP without a login you open to attack. 

If you need super user privileges then you use sudo in terminal or to say run nautilus you would use gksudo nautilus, which would give you a root file browser able to delete anything.

It is not a good idea to be running as root, just use sudo when needed.

Hope this makes sense.

---

### Post by Canew on 2008-01-23
Yes, it makes sense, but just one thing: When you say, "don't run as root," do you mean run as the admin, or a plain vanilla, no privileges user?

---

### Post by philinux on 2008-01-23
When I installed there's just me. So when i login I'm plain vanilla but with admin rights should I need them.

For instance If I want to use synaptic package manager to install some software. I will get asked for my password to do it. This is the superuser password. Get it.

When I want to mess around in the system where i dont have access rights I open a terminal and type gksudo nautilus, now I'm a superuser file browser.

---

### Post by aysiu on 2008-01-23
Think of your computer's system files as money.

One person (let's call her *loggedinasroot*) carries cash with her all the time. She doesn't use a bank.

Another person (let's call her *adminwithsudoprivileges*) has an ATM card and PIN code. The money is in the bank, and when she needs to make a withdrawal, she goes to the ATM and has to authenticate with a password to get the money out.

Then there's a third person (let's call her *adminsyoungchild*), who is not trusted with any money. If she wants something, she asks *adminwithsudoprivileges*, who will then pull money herself and buy the product for *adminsyoungchild*.

Which is it best to run as? Well, don't be *loggedinasroot* for sure.

The *adminwithsudoprivileges* user has pretty good security. I'd make myself *adminsyoungchild* only if I were super paranoid. Of course, if you are that paranoid, you shouldn't be connected to the internet at all...

---

### Post by monte48lowes on 2008-01-23
aysiu,

Very well put.

Mike

---

### Post by mister_pink on 2008-01-23
Just to add to aysiu's post as theres been some confusion about passwords. Each account has its own password. When you were asked for your password it was the one that goes with the account you are logged in as (gonzo), not the root account. The root account, which is litterally called "root", is deactivated by default and I think has no password set (or its set to random characters). Most people will never have any reason to activate the root account - anything you can do as root you can achieve as the admin user, you'll just be prompted for a password or have to use sudo on the command line.

---

### Post by Canew on 2008-01-23
> **mister_pink said:**
> Just to add to aysiu's post as theres been some confusion about passwords. Each account has its own password. When you were asked for your password it was the one that goes with the account you are logged in as (gonzo), not the root account. The root account, which is litterally called "root", is deactivated by default and I think has no password set (or its set to random characters). Most people will never have any reason to activate the root account - anything you can do as root you can achieve as the admin user, you'll just be prompted for a password or have to use sudo on the command line.

Ok, so hopefully the last thing I need clearing up: When I do sudo and it asks for password, it's not looking for a SUPERUSER password, just the CURRENT USER's password as verification?

If that's so, and there really is no root password officially set, do I need to bother with that, or should I just leave it. Is it possible to break something so badly that I'd need to log in as root?

---

### Post by aysiu on 2008-01-23
> **Canew said:**
> Ok, so hopefully the last thing I need clearing up: When I do sudo and it asks for password, it's not looking for a SUPERUSER password, just the CURRENT USER's password as verification? Yes, it's your current user's password.

> If that's so, and there really is no root password officially set, do I need to bother with that, or should I just leave it. Is it possible to break something so badly that I'd need to log in as root? Just leave it as is. If you break something so badly you need to log in as root, that's what recovery mode is for.

---

### Post by Canew on 2008-01-23
Thanks a bunch, guys! This makes a lot more sense now! :)

---

### Post by larochellec on 2008-01-23
Many thanks to Highway for helping me on the root password problem.  You gave me the solution!!!


[I][SIZE="2"]Install as normal, and when installed, log in as the user you setup and type:
sudo passwd root
<enter the user password>
<enter new password for root>
<reenter new password for root>
[/SIZE][/I]

[SIZE="4"]many thanks!![/SIZE]


Claude

---

### Post by meindian523 on 2008-01-24
Now I get why aysiu is admin/moderator and not any other Tom,Dick and Harry.Complete two pages of discussion between Canew,me,dstew and rbc was put beautifully in 1 small case study.No wonder we didn't think of it.

---

### Post by bodhi.zazen on 2008-01-24
> **larochellec said:**
> Many thanks to Highway for helping me on the root password problem.  You gave me the solution!!!


[I][SIZE="2"]Install as normal, and when installed, log in as the user you setup and type:
sudo passwd root
<enter the user password>
<enter new password for root>
<reenter new password for root>
[/SIZE][/I]

[SIZE="4"]many thanks!![/SIZE]


Claude

yea if you come form a su based distro it takes a while to adjust to sudo.

FYI: To lock the root account again :

```
sudo passwd -l root
```

To become root, use sudo -i

```
sudo i
```

To run graphical apps as root, use gksu (kdesu in kde)

```
gksu nautilus
```

At first I was uncomfortable with sudo as I came from a rpm system, but once I learned to configure and use sudo, I now prefer it.

While there is nothing "wrong" with setting a root password if you prefer, it is not necessary to do so. You can configure sudo to use a root password (rather then your user password) if you prefer a separate password for login and sudo use.

---

