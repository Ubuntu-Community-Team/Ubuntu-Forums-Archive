---
title: "How do I update Firefox???"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by kayas80 on 2005-07-23
Hi all

I've gone to about:config and changed general.useragent.vendorsub to 1.0.4. I've added the backport repositries. But I'm still stuck with version 1.0.4. 

I try and apt-get with no luck and synaptic only offers me version 1.0.4.

How do I upgrade to the latest version???

Thanks

Oliver

---

### Post by adwait on 2005-07-23
Try 
sudo apt-get update

Then try
sudo apt-get install mozilla-firefox

---

### Post by kayas80 on 2005-07-23
[QUOTE=adwait]Try 
sudo apt-get update

Then try
sudo apt-get install mozilla-firefox[/QUOTE]


I've tried that and it claims I am using the latest version!!!

---

### Post by timetunnel on 2005-07-23
The latest version 1.0.6. is still (or was yesterday) in the -staging trees of the backports. Look at the paragraph about "Package Testers" at the [Backports](http://backports.ubuntuforums.org/) homepage. It explains what the -staging trees are and how to use them.

Jens

---

### Post by Synt4x_3rr0r on 2005-07-23
[QUOTE=timetunnel]The latest version 1.0.6. is still (or was yesterday) in the -staging trees of the backports. Look at the paragraph about "Package Testers" at the [Backports](http://backports.ubuntuforums.org/) homepage. It explains what the -staging trees are and how to use them.

Jens[/QUOTE]

Does that mean that it will come soon?

---

### Post by timetunnel on 2005-07-23
[QUOTE=Synt4x_3rr0r]Does that mean that it will come soon?[/QUOTE]

Well, it's already there actually if you want to take the "risk" that's described on the backports site I mentioned in my post above. Since I'm quite new to ubuntu as well I have no idea how long it takes for packages to be moved from the -staging tree to the normal backports tree. Anyone?

Jens

---

### Post by poofyhairguy on 2005-07-23
[QUOTE=Synt4x_3rr0r]Does that mean that it will come soon?[/QUOTE]


Yes....a stable version will come soon.

---

### Post by timetunnel on 2005-07-23
Oops, I just realized that is the forum for absolute beginners. Sorry if I confused people with my replies about the -staging tree.
Jens

---

### Post by kayas80 on 2005-07-23
[QUOTE=timetunnel]Oops, I just realized that is the forum for absolute beginners. Sorry if I confused people with my replies about the -staging tree.
Jens[/QUOTE]

I added the staging reposities and it allowed me to update firefox to version  1.0.6.  :smile: The annoying thing is that it crashes every now and again just like version 1.0.4 did.  ](*,) 

Is this a known firefox issue or is it just my setup???

---

### Post by Kvark on 2005-07-23
[QUOTE=kayas80]I added the staging reposities and it allowed me to update firefox to version  1.0.6.  :smile: The annoying thing is that it crashes every now and again just like version 1.0.4 did.  ](*,) 

Is this a known firefox issue or is it just my setup???[/QUOTE]

It might be just your setup. Firefox 1.0.4 is very stable for me. Well, except when it comes to flash/java/other plugins, specially flash seems buggy.

---

### Post by ozzie123 on 2005-07-23
Well that's probably why they put ff 1.0.6 still on the staging tree?

I prefer to manually updated my Firefox installations though...

---

### Post by poofyhairguy on 2005-07-23
[QUOTE=kayas80]I added the staging reposities and it allowed me to update firefox to version  1.0.6.  :smile: The annoying thing is that it crashes every now and again just like version 1.0.4 did.  ](*,) 

Is this a known firefox issue or is it just my setup???[/QUOTE]

Firefox is known for some crashing with me. I use it a lot on many platforms

Sounds like you need an epiphany

> sudo apt-get install epiphany

---

### Post by kayas80 on 2005-07-24
[QUOTE=poofyhairguy]Firefox is known for some crashing with me. I use it a lot on many platforms

Sounds like you need an epiphany[/QUOTE]

What is that and what will it do???

---

### Post by ozzie123 on 2005-07-24
epiphany just doesn't work for me, the program won't even load!

---

### Post by garnertr on 2005-07-24
[QUOTE=kayas80]Hi all

I've gone to about:config and changed general.useragent.vendorsub to 1.0.4. I've added the backport repositries. But I'm still stuck with version 1.0.4. 

I try and apt-get with no luck and synaptic only offers me version 1.0.4.

How do I upgrade to the latest version???

Thanks

Oliver[/QUOTE]




You can go to FIREFOX homepage and d/l the latest debian flavor and then install it yourself.

Place it in your /opt directory; remove the other firefox first and then you'll have the latest greatest... :)

---

