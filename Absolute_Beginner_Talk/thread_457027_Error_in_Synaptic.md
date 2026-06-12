---
title: "Error in Synaptic"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by burt_57 on 2007-05-28
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

---

### Post by Lucifiel on 2007-05-28
Open up Terminal and paste this:

gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 58403026387EE263
gpg --armor --export 387EE263 | sudo apt-key add -

---

### Post by starcraft.man on 2007-05-28
Isn't wine in the main repos of Feisty? Why did ya add that repo, is it special or something? Is it for something else? Now I'm curious... >.>.

Edit: ah, nvm, answered own questions... its the latest builds of wine. Do you really need the latest minute build that bad?

---

