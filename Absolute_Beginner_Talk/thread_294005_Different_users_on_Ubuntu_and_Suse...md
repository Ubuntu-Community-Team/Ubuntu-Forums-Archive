---
title: "Different users on Ubuntu and Suse.."
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-11-06
Hi Folks,
I have Ubuntu Dapper and Suse 10.0 installed on my acer laptop. I have different login names for the two OS'es, so naturally the home folders are different. I copied the mozilla folder from my ubuntu home folder (ill call it 'A') to the Suse home folder ('B'). Everything worked great, my history, extensions etc were all ported to the suse firefox. Now, i want to combine the accounts into one..i.e: have the same folder (A) for both the A and B accounts..How do i go about it?
Thanks,

---

### Post by Joe_CoT on 2006-11-06
If you're suggesting using the same *home* directory for both, i definately do not recommend it.

If you want both to have the same .mozilla directory, that's easy. The easiest way is to make one just a symlink to the other. Pick which one you want to keep, that's userA ; pick the one you want to just be a link, that's userB

```

chmod -R 777 /home/userA/.mozilla
rm -rf /home/userB/.mozilla
ln -s /home/userA/.mozilla /home/userB/.mozilla
```

---

