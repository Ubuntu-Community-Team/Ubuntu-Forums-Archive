---
title: "Xubuntu: how to cancel a print job?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by tico on 2007-08-19
I have sent a job to my printer, but I want to cancel it and cannot figure out how to do that in Xubuntu. My printer is always trying to print it and it doesn't stop trying even if I turn it off.

Any ideas?

Thanks.

---

### Post by schorsch on 2007-08-19
You just typed it ... ;-): The command is "cancel" followed by the id of the print job you want to cancel. This id can be found with "lpstat -t" for example. Please take a look in the manpage of lpstat for other options.

---

### Post by tico on 2007-08-19
> **schorsch said:**
> You just typed it ... ;-): The command is "cancel" followed by the id of the print job you want to cancel. This id can be found with "lpstat -t" for example. Please take a look in the manpage of lpstat for other options.

schorsch,

Thanks for helping. Problem solved. Isn't thera a GUI for doing that? Should I always use terminal to do that in Xubuntu?

Thanks once more.

---

### Post by schorsch on 2007-08-19
Glad to hear that! Could you please mark this thread as solved as this could help others, too?
Regarding your question for a GUI:
System --> Administration --> Printing
Then you get a list of your printers. Right click on printer and choose "Jobs". Under "Edit" you have the option to "Cancel Jobs". Right now I cannot test it but it seems as this is the one you want ... uh, wait, this is it in Ubuntu (Gnome) .... perhaps there is something similar in the administrative area in Xubuntu .... I never run it before ...

---

### Post by tico on 2007-08-19
> perhaps there is something similar in the administrative area in Xubuntu

That's the problem. In Xubuntu I only have "printer configuration - localhost" that doesn't let my see/cancel any job.

Is there other possibility.

PS.: will mark as solved later (hope someone tells me how to get a GUI).

---

### Post by maalmike on 2007-08-28
You may create a laucher with this command:

xfprint4-manager

this launches the printing administrator for xubuntu.

---

### Post by quixotic-cynic on 2007-09-24
I think it is possible to use [http://localhost:631/jobs]("http://localhost:631/jobs") for this.

---

