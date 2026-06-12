---
title: "Updating Wine - Eh?!  remove it first or what?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by jfrancis on 2007-07-24
Hey there,

So I had Wine 0.9.39 installed on my 7.04 ubuntu system.   I see on wine website that version 0.9.41 is out, so want to update.  I look through their help and instructions and end up running this command:

sudo apt-get install wine

After which I am told I have the latest version but when I check, it is shown as 0.9.40.  So, what happened there?  Also, I am not sure if this is the correct way to update.  Am I supposed to remove each version of wine before installing the next?  If so, how do I do this without losing my programs (eve online game actually) cause its a pain to get working?

Any advice/help will be appreciated.

---

### Post by Tomosaur on 2007-07-24
> **jfrancis said:**
> Hey there,

So I had Wine 0.9.39 installed on my 7.04 ubuntu system.   I see on wine website that version 0.9.41 is out, so want to update.  I look through their help and instructions and end up running this command:

sudo apt-get install wine

After which I am told I have the latest version but when I check, it is shown as 0.9.40.  So, what happened there?  Also, I am not sure if this is the correct way to update.  Am I supposed to remove each version of wine before installing the next?  If so, how do I do this without losing my programs (eve online game actually) cause its a pain to get working?

Any advice/help will be appreciated.

The repositories may not have updated to 0.9.41 yet. You will have the latest version which is available from the repositories. You can, of course, install the latest version manually from the wine website.

---

### Post by Mornedhel on 2007-07-24
You don't have to uninstall a package before upgrading to the latest version. The problem is, the Ubuntu repositories usually don't have the bleeding edge versions of software (for excellent dependency reasons). If you absolutely need the latest Wine, try getting a .deb package for it somewhere, and double-click it once downloaded.

---

### Post by Majorix on 2007-07-24
You are supposed to update using their repo. Add it and then install wine like this: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Hope it helps. Good luck!

---

### Post by jfrancis on 2007-07-24
Thanks you guys, this is starting to make more sense.

However, I did add their repos as shown in the link above so not sure what happened there. No worries though, I was mainly concerned that I should had removed it first before upgrading, but that is not true.  Thanks!

---

### Post by jfrancis on 2007-07-24
OK, here is another question because I am confused!

At terminal, when I type wine --version it reports that it is:

wine-0.9.40

But when I go in to Synaptic Package Manager and look up wine, it shows that I have version 0.9.41 installed ???!!!!

So... how do I really know which version I have?

Cheers!

---

### Post by bodhi.zazen on 2007-07-24
Not that it helps, but there is another (unanswered) thread here asking the same question ...

Perhaps you could ask on #wine

---

### Post by jfrancis on 2007-07-24
Ah.. well in that case, can you tell me how to completely remove it?  Then I can install it fresh and then I will know it is the latest version.

Cheers!

---

### Post by bodhi.zazen on 2007-07-24
You can remove it via synaptic or the command line ...

sudo apt-get remove --purge wine && apt-get install wine

---

### Post by jfrancis on 2007-07-24
When purging files, it won't do it for permission reasons.  It asks me if I am root?

How do I get round this?  I entered my password (from using command sudo) so I thought that would be enough.

Thanks btw.. much appreciated.

---

### Post by bodhi.zazen on 2007-07-24
Odd ...

You can always just 

sudo apt-get remove wine && apt-get install wine

---

