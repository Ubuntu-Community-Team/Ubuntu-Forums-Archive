---
title: "[SOLVED] Deluge"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by teh'p3nsi0n3r on 2007-10-21
goes to start, i see it trying to update "the blocklist" although i dont think i set this up correctly then the program closes, ive removed it then reinstall it from repos., does the same, ive removed it again and installed the latest gutsy release from the deluge website, still the same apart from it went through the setup configuration screen then starts up then closes.

---

### Post by bumanie on 2007-10-22
Which blocklist did you enable? I have found the peerguardian blocklist hangs and does nothing. Try the bluetack blocklist instead. To do this you may have to uninstall and reinstall it.

---

### Post by teh'p3nsi0n3r on 2007-10-22
hi, i think it was the peergaurdian one, it did hang, but deluge program closes before i can do anything in other words it shuts down by intself after it tried to update the blocklist, i have tried removing deluge as i mentioned in my last post a few times, still not working.:confused:

---

### Post by philinux on 2007-10-22
Thats because it must be retaining its config files somewhere. These need deleting.

---

### Post by teh'p3nsi0n3r on 2007-10-22
i had that assumption do you know where these config files are kept?

thanks.

---

### Post by philinux on 2007-10-22
Just been poking around - hope this helps.

---

### Post by Maestro23 on 2007-10-22
> **teh'p3nsi0n3r said:**
> i had that assumption do you know where these config files are kept?

thanks.

Hidden directory in your /home/username

> ls -a

Lists all directories/files. (hidden directories have a "." in front of them)

Look for Deluge's then delete.

---

### Post by bumanie on 2007-10-22
Have you tried to remove the config via this command?
rm -Rf ~/.config/deluge/
This is meant to remove all old config files prior to upgrading. May be worth a try.

---

### Post by teh'p3nsi0n3r on 2007-10-22
thanks phillinux, i took a look into that dir, no dleuge files this was the 1st place i looked same with your idea there maestro, one of the 1st things i checked, this is why i was confused, i tried your idea bumanie, ran that command in the terminal, and it worked after reinstalling deluge. everything working now thanks! :)

---

### Post by Maestro23 on 2007-10-22
> **teh'p3nsi0n3r said:**
> thanks phillinux, i took a look into that dir, no dleuge files this was the 1st place i looked same with your idea there maestro, one of the 1st things i checked, this is why i was confused, i tried your idea bumanie, ran that command in the terminal, and it worked after reinstalling deluge. everything working now thanks! :)

Good deal.  Please mark this thread SOLVED vai the Thread Tools.

Thanks. :)

---

### Post by teh'p3nsi0n3r on 2007-10-22
done :)

---

