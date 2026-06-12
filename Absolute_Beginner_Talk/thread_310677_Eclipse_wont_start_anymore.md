---
title: "Eclipse wont start anymore"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Cruz on 2006-12-01
Hello people,

I was using Eclipse for a couple of days. Today it stopped working, well it kind of froze. I looked at "top" and saw thet gcj is eating ALL my memory. Then at some point the system said to me that eclipse is not responding and if it should be shot down even if it means losing unsaved files. I said yes to that. And now it wouldn't start anymore. When I try it says I should take a look into the workspace/.metadata/.log file. Well I did that and it says there: 

!ENTRY org.eclipse.core.resources 2 10035 2006-12-01 22:29:46.394
!MESSAGE A workspace crash was detected. The previous session did not exit normally.


A great help that is. 

Alright, I tried completely removing and reinstalling Eclipse with synaptic. I also tried switching to the sun JVM but nothing helps. The same error message every time. Any ideas what I can do?

Thanks 
Cruz

---

### Post by Adramelech on 2006-12-01
Never used eclipse, but maybe deleting the configuration files for eclipse on ~/ may work.

---

### Post by tanguyr on 2007-02-25
Hello,

I have the same basic problem as the op, except i am running on sun 1.5. I have also tried the remove/reinstall of eclipse and java no joy. I tried the "remove ~/.eclipse" advice of the parent, and there is definitely something to it: you get asked to choose a workspace and eclipse does come up - albeit with some error messages.

Regs,
/t

---

### Post by jblaster on 2008-02-19
I had the sort of problem: Eclipse would say there was an error and to check the log file whenever I started up the app. I think it was a problem with my workspace folder because when I deleted the ~/.eclipse folder and eclipse booted no problem and asked for a new workspace (I'm not saying that it was a workspace problem because it prompted for a new one, its because when I selected a different workspace folder from the previous one it worked).

---

