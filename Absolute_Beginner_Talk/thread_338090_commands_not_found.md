---
title: "commands not found????"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-01-14
Hi I recently purchased 'The Linux Cookbook' and have started reading it, however to my suprise commands that are mentioned in the book which could be quiet helpful are coming up as 'command not found'. For example, when I type 'emacs' in the terminal it can't be found??? Is this a problem or does it just not come with Ubuntu. Maybe I'm missing files??? But I don't know how I just recently clean installed Ubuntu Dapper.

---

### Post by NeoLithium on 2007-01-14
It's not missing files, persay; sometimes you don't have the programs yet that they are using, an example for emacs, would be just ```
sudo aptitude install emacs
``` and you'll be able to use it.

---

### Post by nite owl on 2007-01-14
Thankyou for your reply NeoLithium, But it's also not recognising some commands not just programs stated in the book i.e. compress.. etc. coming up as 'command not found'??.

---

### Post by confused57 on 2007-01-14
> **nite owl said:**
> Thankyou for your reply NeoLithium, But it's also not recognising some commands not just programs stated in the book i.e. compress.. etc. coming up as 'command not found'??.
As NeoLithium said, evidently the programs are not installed in Ubuntu for the commands you're entering...emacs is a text editor, Ubuntu has nano(as does most Linux distros) and gedit, those are the 2 that I use...nano for console & gedit for GUI.

What you can do is open Synaptic Package Manager, type the command in the Search tool, and install the program, if  it's available through the repos.

---

### Post by nite owl on 2007-01-14
Oh ok thanks for your help :)...was just confused as to why the commands suggested in the book were not working. Thanks

---

