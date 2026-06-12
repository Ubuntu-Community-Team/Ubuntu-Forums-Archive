---
title: "Environment Variables in UI Launched Applications"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by HurricaneDavid on 2007-12-17
I am trying to set some environment variables that will be picked up by an application that is launched when I click on an icon (customer application launcher) on a panel.

I can set the environment variables in by .bashrc file and they are correctly picked up when I run the command from the terminal window. But when I launch my application by clicking on the icon, it does not pickup the environment variables (the application isn't running the .bashrc).

Is there a place on my system where I can set the environment variables such that they will be picked up in both my terminal windows AND my applications launched from the GIU?

Thanks in advance,
David

---

### Post by Cypher on 2007-12-18
The .bashrc file is processed when you open a terminal so any application run within that terminal will have access to those varialbles. When you launch them seperately from the panel/desktop, if it's a regular application it will be not be launched in the context of BASH, so the environment variables won't show up.

What kind of application are you playing with here?

---

### Post by erginemr on 2007-12-18
You can "instruct" the application to use the environment value you desire by inserting the following phrase in to its shortcut:
```
env (Env_Name)=(Env_Value)  (shortcut command) 
```
all without parantheses.
 
For instance, due to a bug in Totem in Gutsy, I cannot start in in my language (Turkish, so LANG=tr_TR.UTF-8) settings. So, I had to use the following command in its shortcut, to dupe it that the local language is English:

```
env LANG=en_EN.UTF-8 totem
```

I hope this is what you are looking for.

---

### Post by HurricaneDavid on 2007-12-19
Thanks for the help. The environment variable message worked.

I will answer the question about what I am doing so that someone may suggest a better way.

I need to have three versions of the JAVA jdk installed (1.4.2, 5, and 6). In addition, I need to run the latest version of eclipse (3.3.1.1).

So I created separate directories for the JDKs and installed eclipse myself (I did not use apt-get for any of the above).

So I need to set my JAVA_HOME and modify my PATH environment variables before I launch eclipse.

It seems like there should be a .xxxrc or .profile somewhere to which I could add these entries such that every application launched from the panel would receive them.

I am coming from a windows environment where this would be the equivalent of GLOBAL variables.

Any suggestions would be appreciated.

---

### Post by erginemr on 2007-12-19
> **HurricaneDavid said:**
> I am trying to set some environment variables that will be picked up by an application that is launched when I click on an icon (customer application launcher) on a panel.

I can set the environment variables in by .bashrc file and they are correctly picked up when I run the command from the terminal window. But when I launch my application by clicking on the icon, it does not pickup the environment variables (the application isn't running the .bashrc).

Is there a place on my system where I can set the environment variables such that they will be picked up in both my terminal windows AND my applications launched from the GIU?

Thanks in advance,
David

Did you also try inserting the environment variables into your "~/.profile" in your home directory, as compared to .bashrc?

set YOURVARIABLE=thevalue
or export YOURVARIABLE=thevalue

---

### Post by HurricaneDavid on 2007-12-20
The ~/.profile suggestion worked like a charm. THANKS!

The comment in the header of that file threw me for a loop, so I didn't try to modify it before:

```
This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login exists.
```

It appears the ~/.profile script is executed when I login (which is nice). Any modifications to that script are not picked up until I login again.

Also, I noticed that I must **export** new environment variables, but I can change existing environment variables (or the **PATH** variable at least). To illustrate this, here is what I added to my ~/.profile:

```

export JAVA_HOME=/tools/jsdk/1.5
PATH=${JAVA_HOME}/bin:"${PATH}"

```

Thanks for the help!

---

