---
title: "Crontab is driving me NUTS!"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by JetSirus on 2007-05-27
**EDIT:  Most everything fixed now.  All I need to know now is how to specify a xorg screen for zenity so it will work with cron.  Any help appreciated.**

I have been trying forever to get crontab to work.  When I edit it with "crontab -e" it recognizes the changes, but the file "/etc/crontab" has not changed.  Is that just the file that cron reads when the system first boots?  Secondly, whenever I edit crontab with "crontab -e" it recognizes the changes but fails to implement them, IE nothing happens.  

What I am trying to do is have crontab shutdown the computer every night at 4 am and pop up a warning message box with zenity (this system will always have gnome running).  To test and see if this would work I inserted a zenity command into crontab to activate every minute.  Nothing happens.  Following are all the relevant files.

**RESULT OF:** crontab -l
```
jetsirus@hampton-desktop:~$ crontab -l
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

# Show a message box every minute.
* *     * * * root zenity --warning --title "Test" --text "Test"

```
**NET EFFECT OF LAST LINE:** Nothing
**DESIRED EFFECT OF LAST LINE: ** Warning box with the title of "test" and the contents of "test".

**CONTENTS OF:** /etc/crontab
```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
```
This is the default ubuntu version of "/etc/crontab".

**DESIRED CONTENTS OF: **/etc/crontab
```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

# Run daily shutdown sequence.
0 4	* * *	root zenity --warning --title "Computer Restarting" --text "System restarting for daily maintenance in one minute." && shutdown +1 -r "Restart in one minute."
```
**NET EFFECT OF LAST LINE:** Nothing
**DESIRED EFFECT OF LAST LINE:**  Warning box with the title of "Computer Restarting" and the contents of "System restarting for daily maintenance in one minute."  When that box is closed the shutdown event begins, and finally the computer reboots after one minute.

Thanks for any help you can offer.  This is driving me mad.

---

### Post by Nikron on 2007-05-27
Probably because zenity isn't finding a screen..  Then, it returns an error message causing the next part of the && statement not to work.  Try  ' echo "Hello world!" | wall ' and open up a terminal.

---

### Post by JetSirus on 2007-05-27
> **Nikron said:**
> Probably because zenity isn't finding a screen.. Then, it returns an error message causing the next part of the && statement not to work. Try ' echo "Hello world!" | wall ' and open up a terminal.

I know Cron runs behind almost everything else.  You don't even need to be logged in for it to work I think, but can I get this functionality out of it?

EDIT:  The echo "Hellow world!" | wall works if I remove the exclamation point.  Well it works in a way.  The console displays an empty message.

---

### Post by Nikron on 2007-05-27
> **JetSirus said:**
> I know Cron runs behind almost everything else.  You don't even need to be logged in for it to work I think, but can I get this functionality out of it?

EDIT:  The echo "Hellow world!" | wall works if I remove the exclamation point.  Well it works in a way.  The console displays an empty message.

To get zenity to work you need to specfiy a xorg screen, I can't remember how to off the top of my head though, sorry.

---

### Post by JetSirus on 2007-05-27
> **Nikron said:**
> To get zenity to work you need to specfiy a xorg screen, I can't remember how to off the top of my head though, sorry.

Thanks for the lead on the problem though.  Maybe someone else might know?

---

### Post by Pollywoggy on 2007-05-27
The command 'crontab -e' is for user crontabs and the root user crontab.  It does not affect /etc/crontab

You modify /etc/crontab directly

---

### Post by JetSirus on 2007-05-27
> **Pollywoggy said:**
> The command 'crontab -e' is for user crontabs and the root user crontab.  It does not affect /etc/crontab

You modify /etc/crontab directly

Thanks!  I was wondering what the deal was.  Anyone know how to specify a xorg screen for zenity?

---

### Post by JetSirus on 2007-05-28
Bumpity bump bump.

---

### Post by j85wilson on 2007-06-28
DISPLAY=:0 zenity --foo "bar"

---

