---
title: "how to uninstall cedega - problem"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by sk3jt on 2007-02-07
hello - first of all excuse my poor English - and now for the post - I need HELP - I installed Cedega from a .deb file - and now I would like to uninstall it but it does not show in the add/remove tool :( Please HELP me! I'm a total Linux noobie...

---

### Post by muguwmp67 on 2007-02-07
From [http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm]("http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm")

To uninstall a .deb file, deselect it in your package manager, or type:

    sudo dpkg -r package_name

---

### Post by sk3jt on 2007-02-07
okay - i tryed that but it did not work everything i get is:

sk3jt@sk3jt-laptop:~$ sudo dpkg -r cedega
Password:
dpkg - warning: ignoring request to remove cedega which isn't installed.

the file i used is called:

cedega-small_5.2.3_all.deb

but when i type in the terminal:

sudo dpkg -r cedega-small_5.2.3_all

all i get is:

sk3jt@sk3jt-laptop:~$ sudo dpkg -r cedega-small_5.2.3_all
dpkg - warning: ignoring request to remove cedega-small_5.2.3_all which isn't installed.

am i really too stupid to uninstall a simple app ?? PLEASE HELP!

thanks muguwmp67

---

### Post by Dayylin on 2007-02-07
Hi there, have you checked the forums at transgaming? [http://transgaming.org/forum/]("http://transgaming.org/forum/") lots of good info there.

---

### Post by muguwmp67 on 2007-02-07
Did cedega successfully install?

Try
sudo -l cedega*

(Thats an 'l' as in 'list')

Is it listed?  Try uninstalling the package name that it shows, if it is shown.

---

### Post by sk3jt on 2007-02-07
okay - thanks again

this time i tryed:

sudo -l cedega*

everything i got is:

sk3jt@sk3jt-laptop:~$ sudo -l cedega*
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
                  { -e file [...] | -i | -s | <command> }

so i guess I had to install it wrong - but it worked - a bit - do you have any other advice - i don't know where to turn...

oh - and on the transgaming forum i found a lot of information on how to install cedega but none on how to uninstall that damn thing 

still NEED HELP - THANKFUL 4 EVERY ADVICE

---

### Post by muguwmp67 on 2007-02-07
My bad:

sudo dpkg -l cedega*

to see if it installed.

---

### Post by sk3jt on 2007-02-07
yep! that was what i needed

thanks muguwmp67 :)

---

