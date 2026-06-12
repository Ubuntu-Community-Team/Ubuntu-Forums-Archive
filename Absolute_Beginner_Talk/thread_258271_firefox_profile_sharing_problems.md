---
title: "firefox profile sharing problems"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by lintroduccion on 2006-09-15
I had already installed several extensions and have many bookmarks in firefox when I got Xubuntu. So I decided it was better to share my profile between them.

I managed to install fs-drive in my windows xp and I created a profile in my ubuntu's firefox pointing to the directory I want it to use. That's how it works, right?:confused: 

Now, the problem is that every time I try to open firefox in Ubuntu a message appears, that says "an another instance of firefox is running", which is very strange because I haven't executed anything before that.

I can only load the program by sudo-ing in the terminal, but it doesn't give me the needed extensions and bookmarks... plus, what if I mess up something?

I think that an extension's got to be the problem.
Something like... sessionmanager?](*,) 

It did ever happen to anyone?

---

### Post by mitch.c on 2006-09-15
> **lintroduccion said:**
> Now, the problem is that every time I try to open firefox in Ubuntu a message appears, that says "an another instance of firefox is running", which is very strange because I haven't executed anything before that.

```
ps ax | grep firefox
```
Make sure firefox isn't running. If it is kill the PID.

If you are sharing a profile between machines, is firefox running on the other machine? Is there a file called lock in your profile? If so, delete and try running firefox again.

---

### Post by lintroduccion on 2006-09-15
> **mitch.c said:**
> ```
ps ax | grep firefox
```
Make sure firefox isn't running. If it is kill the PID.

If you are sharing a profile between machines, is firefox running on the other machine? Is there a file called lock in your profile? If so, delete and try running firefox again.

OK... So I have to run that command to figure out firefox's PID without having firefox running on background, and then kill it by "kill #", for example, "kill 5042", right?

I rebooted Xubuntu and tried the code, but it said no such process exists...

```
asdf@asdfqwerzxcv:~$ ps ax | grep firefox
 5854 pts/1    S+     0:00 grep firefox
asdf@asdfqwerzxcv:~$ kill 5854
bash: kill: (5854) - &#44536;&#47088; &#54532;&#47196;&#49464;&#49828;&#44032; &#50630;&#51020;

```

I'm not sharing my profile with other computers. I have just one computer with 3 partitions, one for Ubuntu, another one for windows xp, and the other one is a shared partition (ext3). I found no file called lock in my profile.

---

### Post by mitch.c on 2006-09-15
> **lintroduccion said:**
> OK... So I have to run that command to figure out firefox's PID without having firefox running on background, and then kill it by "kill #", for example, "kill 5042", right?

I rebooted Xubuntu and tried the code, but it said no such process exists...

```
asdf@asdfqwerzxcv:~$ ps ax | grep firefox
 5854 pts/1    S+     0:00 grep firefox
asdf@asdfqwerzxcv:~$ kill 5854
bash: kill: (5854) - &#44536;&#47088; &#54532;&#47196;&#49464;&#49828;&#44032; &#50630;&#51020;

```

I'm not sharing my profile with other computers. I have just one computer with 3 partitions, one for Ubuntu, another one for windows xp, and the other one is a shared partition (ext3). I found no file called lock in my profile.

Why don't you see if you can create a new profile. You can copy your bookmarks from the old profile to the new, and then reload your extensions one by one, making sure firefox starts after each one.

1. Hit <Alt> + <F2> and type: firefox -profilemanager
2. Create a new profile.
3. Close firefox
4. Copy bookmarks.html from your old profile
5. Start firefox.
6. Load and test extensions.

---

### Post by lintroduccion on 2006-09-16
Phew... finally it's working:).
I created a new profile from Ubuntu and pointed it from Windows.

There's something strange I noticed; Firefox couldn't start ("another instance of firefox running") when the profile points to a directory out of /home/[username]/.mozilla/firefox. I moved my previous profiles into the "right" path and it suddenly worked!:confused: 

Well, at least it's running fine. Just a minor annoyance, though. Firefox checks for my extensions compatibility whenever it's Ubuntu or Windows. How can I turn off that?

---

### Post by crossedout on 2006-09-16
> Firefox checks for my extensions compatibility whenever it's Ubuntu or Windows. How can I turn off that?

That is undoubtedly happening b/c your versions don't match.  FF in Ubuntu is 1.5.0.5 & FF in Win is 1.5.0.6.  Until the versions coincide I don't believe there is a way to disable the message.  However, there is a new update that should be added for both systems (1.5.0.7) very soon.  When you receive the update message(s), make sure you update and they should resolve the 'compatibility' message.

-Xout

---

### Post by lintroduccion on 2006-09-17
Now everything makes sense:).
Thanks for the kind help!

---

