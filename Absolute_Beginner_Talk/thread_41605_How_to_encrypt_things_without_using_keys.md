---
title: "How to encrypt things without using keys??"
date: 2005-06-14
forum: Absolute Beginner Talk
---

### Post by wowbuntu on 2005-06-14
Hi all

Is there any nice app in Ubuntu/Kubuntu by which I can encrypt files & folders WITHOUT using keys? I find this key system of KGpg quite compilcated & incomprehensible. 
And I think KGpg can only use keys to encrypt right?
How do I encrypt things simply with a password? Is this possible with any of the default apps of Ubuntu/Kubuntu?

Plz help.

Love
Newbie

---

### Post by eyequeue on 2005-06-14
[QUOTE=wowbuntu]
How do I encrypt things simply with a password? Is this possible with any of the default apps of Ubuntu/Kubuntu?
[/QUOTE]

I suspect you're referring to public/private keypairs.

Perhaps you're looking for a command like this?

```
$ gpg --symmetric foo
``` which will encrypt the contents of a file named "foo" and create a file named "foo.gpg". You would then ```
$ rm foo
``` to delete the original cleartext file.

To decode this, you would ```
$ gpg foo.gpg
``` which will prompt you for the same passphrase you originally used, and then place the decrypted cleartext in a file named "foo".

---

### Post by eyequeue on 2005-06-14
[QUOTE=eyequeue]I suspect you're referring to public/private keypairs.[/QUOTE]

Technically, the passphrase you issue is considered a (symmetric) key, but I've interpreted your request to be only to avoid (asymmetric) public/private style keypairs.

If the example above doesn't accomplish what you wanted, let me know.

---

### Post by wowbuntu on 2005-06-15
[QUOTE=eyequeue]Technically, the passphrase you issue is considered a (symmetric) key, but I've interpreted your request to be only to avoid (asymmetric) public/private style keypairs.

If the example above doesn't accomplish what you wanted, let me know.[/QUOTE]
 Isn't there a nice GUI way instead of through commands?
No app can do this GUI-way??

---

### Post by desdinova on 2005-06-15
In KDE - Install kgpg and it'll add right click options to Konqueror

---

### Post by desdinova on 2005-06-15
And in Gnome GPA does roughly the same (a quick tip may be before asking the question to have a quick search in Synaptic - I have gpa installed and I've used kgpg in the past)

---

### Post by Alexander Kirillov on 2005-06-15
[QUOTE=wowbuntu]Isn't there a nice GUI way instead of through commands?
No app can do this GUI-way??[/QUOTE]
 Try seahorse. It is available as a package in universe repository.

---

### Post by kerinin on 2006-02-11
i don't believe any of these programs will actually do a symmetric file encryption from within the gui.  maybe (hopefully) i'm wrong, but i haven't been able to figure that out yet.

---

### Post by cwaldbieser on 2006-02-11
[QUOTE=kerinin]i don't believe any of these programs will actually do a symmetric file encryption from within the gui.  maybe (hopefully) i'm wrong, but i haven't been able to figure that out yet.[/QUOTE]
KGpg does.  When you choose to encrypt the file, just choose the Options button and check off "Symmetric Encryption".

---

