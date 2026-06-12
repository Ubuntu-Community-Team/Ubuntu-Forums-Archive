---
title: "extra repositories"
date: 2005-08-27
forum: Absolute Beginner Talk
---

### Post by servvs on 2005-08-27
Ok... i followed the guide and typed...

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

... i think i accedentally overwrote something i wasnt supposed to in the .list thing. can someone go to it and copy and paste what the whole thing looks like? or email what it looks like [email]servvs@gmail.com[/email].

---

### Post by essexman on 2005-08-27
[QUOTE=servvs]Ok... i followed the guide and typed...

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

... i think i accedentally overwrote something i wasnt supposed to in the .list thing. can someone go to it and copy and paste what the whole thing looks like? or email what it looks like [email]servvs@gmail.com[/email].[/QUOTE]

You can cut and paste from the [Ubuntu Guide](http://www.ubuntuguide.org/#extrarepositories) section on extra repositories.  Being dyspraxic (crap at typing amongst other things) I cut and past code from instructions where ever possible and the Ubuntu guide and wiki howtos are great for doing this.

All the best

Essexman

"Excuse me, do you have extra repositories?" "No, it's just the way I walk!" ;-)

---

### Post by racecat on 2005-08-27
I'll take a stab at this. The first command (cp) is a copy command to back up the file in case something went wrong. I think you just do a "sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list" to restore the file. I believe that you end up replacing all but the first line in the file when you (suggested method) highlight, copy, and paste the dialogue over the old verbage.

When you open Synaptic for the first time after changing sources.list, you will get an error. I don't remember exactly what the error is, but I believe it is because the sources.list doesn't match the available packages list (just a guess - somebody who knows please help clarify) until you "reload".

Hope this helps.
Bill

---

