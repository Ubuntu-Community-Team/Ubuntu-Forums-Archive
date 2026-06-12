---
title: "I want to use (k)ubuntu!"
date: 2005-07-07
forum: Absolute Beginner Talk
---

### Post by chivas on 2005-07-07
Howdy all.
I just got me a new laptop (my first one) and decided to try kubuntu since I heard so much fuss about ubuntu on laptops (detecting everything and all).
However I have some issues with the way ubuntu works that I need to get accustomed to, and decided maybe someone here can shed some light on them. I previously used redhat, mandrake and gentoo if that helps.

1. First of all where do I go for info on how the packages are managed? For example I had to add multiverse in /etc/apt/sources.list to get openoffice.org2 to show up (which is treated as a different app from openoffice.org). 

2. How would I go about installing a custom package? Suppose I find something on kde-look that I really want. Does the author need to provide a .deb file or a link I add to sources.list? In other distros it was an ebuild or an rpm, but here I am lost.

3. Speaking of which ... what happens when the same product is on two lines in sources.list? Do I get a choice of installing from a source or the other? Is this possible at all?

4. Is it possible to install a specific version of an app? say I have gnome-2.10 available and this is installed when I do apt-get install gnome, but I want gnome-2.2 (just an example).

5. One last question for now: I tried to remove postfix and it also tries to remove ubuntu-desktop. Don't other apps *need* it?

---EDIT ADDED PARAGRAPHS AS PER REQUESTED---

---

### Post by sapo on 2005-07-07
1 - To install a custom package you have to run in a terminal: dpkg -i package.deb, but you can install tarballs and even rpm (using alien to convert it to .deb and then install with dpkg).

2 - openoffice.org is different from openoffice.org2 cause ubuntu doesnt have the version 2 (still beta) of this package.. so you have added another source that provides it and they are 2 different packages.

3 - Is possible to install a package using the source.. but dont ask me how.. never did it.  :roll: 

4 - You can install another version of some apps.. but if you try to install gnome 2.2 you will have to remove all the packages that depends on gnome 2.10.. so.. thats not a wise thing to do.  ](*,) 

5 - ou can remove the ubuntu-desktop without problems.. this package is just a dummy packages that depends on ALL the ubuntu default desktop apps...

6 - Please.. help us answering your questions.. use paragraphs in your text.. sorry if i forgot something  :roll:

---

### Post by chivas on 2005-07-07
[QUOTE=sapo]1 - To install a custom package you have to run in a terminal: dpkg -i package.deb, but you can install tarballs and even rpm (using alien to convert it to .deb and then install with dpkg).

2 - openoffice.org is different from openoffice.org2 cause ubuntu doesnt have the version 2 (still beta) of this package.. so you have added another source that provides it and they are 2 different packages.

3 - Is possible to install a package using the source.. but dont ask me how.. never did it.  :roll: 

4 - You can install another version of some apps.. but if you try to install gnome 2.2 you will have to remove all the packages that depends on gnome 2.10.. so.. thats not a wise thing to do.  ](*,) 

5 - ou can remove the ubuntu-desktop without problems.. this package is just a dummy packages that depends on ALL the ubuntu default desktop apps...

6 - Please.. help us answering your questions.. use paragraphs in your text.. sorry if i forgot something  :roll:[/QUOTE]

Thank you!

4. It was just an example ... but how would I do that? Things are still a bit unclear to me as far as versioning goes in ubuntu. Isn't there some guide to apt-* and the dpkg command (just heard about it from you) and others that might be lurking around there?

5. Anywhere I might go to find out about dependencies in ubuntu?

6. Done

---

### Post by manicka on 2005-07-07
[QUOTE=chivas]Thank you!

4. It was just an example ... but how would I do that? Things are still a bit unclear to me as far as versioning goes in ubuntu. Isn't there some guide to apt-* and the dpkg command (just heard about it from you) and others that might be lurking around there?

5. Anywhere I might go to find out about dependencies in ubuntu?

[/QUOTE]

4. Synaptic (not sure about Kynaptic) gives you options to control the version that will be installed.

5. Apt or synaptic will handle most of your dependency problems

---

### Post by Lord Illidan on 2005-07-07
I also use Synaptic..Believe me, don't get kynaptic, although it has a KDE interface, it is nowhere as powerful as Synaptic...

I am a Kubuntu user like you, and I have encountered no problems with it..(apart from the mistakes I did when not reading the manuals...(do some research, it will serve you well.))

---

### Post by chivas on 2005-07-07
Howdy again.
Well I'm sorry to say I decided kubuntu may not be for me at this stage. So I'll try something else (no sense telling what it is) that's also along the lines of kde and laptop.
Thank those of you who have replied for your time.

Good luck!

---

