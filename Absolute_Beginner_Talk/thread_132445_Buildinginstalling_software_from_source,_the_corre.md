---
title: "Building/installing software from source, the correct way to do it?"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by speedsix on 2006-02-18
Ok so let's say I want a piece of the software that requires me to build it from source because it's either not in the repositories or I want the very latest version.

At the moment I'm downloading the source .tar file, compiling and installing as per the instructions but obviously this is all completely outside the apt/synaptic system which isn't really desirable. Is there a way to have everything go through synaptic maybe by packing things into .deb files and keep dependencies etc intact?

For example let's say I want to update my version of Xine to the latest from the website, can I somehow compile & package this so all the programs that depend on Xine still work and I don't have to remove them when I remove the original Xine from synaptic, if that makes sense?

Many thanks

Dom.

---

### Post by stalefries on 2006-02-18
At the point when you are supposed to "sudo make install" do a "checkinstall" instead. THat will create a .deb, which you can then install with "sudo dpkg -i <filename>.deb" 

Hope this helps!

---

