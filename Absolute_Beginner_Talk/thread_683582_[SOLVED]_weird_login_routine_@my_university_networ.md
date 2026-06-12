---
title: "[SOLVED] weird login routine @my university network -workarounds?"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by soleille on 2008-01-31
At my university, you need to log in to use the internet using your "customer" number and password. Windows users get a nifty little login client where you can save this info and connect with one click. Linux users have to type ssh -l (number)  (Ip address) into the terminal, then are prompted to enter the PW.

Is there an easy (maybe even GUI?) way to automate this? I don't know any commands except rm :oP and don't feel confident fiddling a lot - if there's an easy command way, please walk me through every step- if it's not advisable for a bloody beginner, just tell me to stick with opening a text file and copying the lines like I do now :O)

---

### Post by p_quarles on 2008-01-31
I wouldn't advise automating the password entry, but you can easily automate the ssh command itself by adding an alias to your profile. Open your .bashrc file in a text editor, and add a line like this:
```
alias login='ssh -l (number)  (Ip address)'
```
You will now be able to type "login" to run the entire command.

---

### Post by Anicka on 2008-01-31
You could make and alias for the "ssh -l" thingy. There is a hidden file called ~/.bash_profile. Open it with your favourite texteditor and put in on a new line: ```
alias unilogin='ssh -l (number) (IP)'
``` (unilogin could be any word that isn't already used by the system, "login" is fx already taken). Open a terminal and type unilogin, and you should only have to put in your password, how to get rid of that step, someone else will have to figure out...

Good luck!

---

### Post by soleille on 2008-01-31
Thank you, I will do that - once I find the file in question - where exactly is that? Tracker doesn't find it...

Also, as for saving the password - nobody but me has access to this computer, and as the password is a random string impossible to remember, surely automating it wouldn't be more unsafe than having a text file with the PW sitting on my desktop?

---

### Post by emarkd on 2008-01-31
The file is in your home directory, but it's hidden.  Open the File Browser (Nautilus), click on View and select Show Hidden Files.

---

### Post by hyper_ch on 2008-01-31
```

gedit ~/.bashrc

```

---

### Post by soleille on 2008-01-31
Thanks, this works like a charm:o)
Now I either need someone to help me with the password thingy or install additional memory in my brain :o)

---

### Post by Joeb454 on 2008-01-31
What issue are you having with the password thingy? It'd be a lot more secure to just remember it.

If you can change it, then do so to something memorable, that way nobody can log in as you, even if they use your PC

---

### Post by soleille on 2008-01-31
Unfortunately, the PW can't be changed, and it's horrible- the windows client save option was a godsent. And access to my computer, especially in my dorm, only happens over my cold dead body :o)
But if you all really don't want to tell me, I'll have to stick to my copy routine anyway :o)

---

### Post by Joeb454 on 2008-01-31
Actually I'm not sure if there is a way to auto-send the password via an ssh protocol.

I'll look into it more, but the ssh man page doesn't tell you much about it.

```
man ssh
``` if you want to look yourself :)

---

