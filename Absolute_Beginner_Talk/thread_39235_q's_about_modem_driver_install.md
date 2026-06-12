---
title: "q's about modem driver install"
date: 2005-06-03
forum: Absolute Beginner Talk
---

### Post by diogena on 2005-06-03
I've been to the Linuxant pages and downloaded and burned to cd the hcfpcimodem package.

I printed out the installation instructions, but when I follow them to the letter, replacing the word version with v.92, (hence my terminal command becomes dpkg -i hcfipcimodem_{v.92}_{arch}.deb) I get an error message-something about something not existing.

I've been looking online for a week now for better instructions for me because I am so new to unix line commands that I am sure I am missing steps, but I haven't found any help.

Some people might say I am trying to walk before I learn to crawl, but I had no real trouble installing Ubuntu for a dual boot environment, making my old laser printer print in Ubuntu, and so I think it isn't too much to ask to be able to try out that conexant driver and consider purchasing it for my winmodem. I am sure of the type of winmodem I have. I want to try this before breaking down and buying a real serial modem. I believe I would learn abundantly from seeing the complete command for installing the driver.

I keep coming across the same kind of info--I now have O'Reilly's Linux Pocket Guide--basic commands or advanced commands, but no instructions on the series of steps involved in installing linux drivers from downloads burned to cds.

I did get a package with a question mark on it with the suffix .deb copied to cd.

I tried to follow my instincts on using the archive manager and those driver files all appeared to go into a folder labeled . so the location appears to be /./

Could someone out there just please tell me what to type in the terminal, starting at my log in prompt, with the files waiting on the cd in the drive? I assume I begin with sudo....

In the meantime I will keep trying to figure this out for myself, but I suspect that I will try something that will make a mess of my file system somehow and I will have to reinstall Ubuntu....or another distro.

Now here is a question that might make me decide to give up entirely on the linuxant experiment. If I successfully install the linux driver for this winmodem, will it stop working in Windows? I assume not, but yes or no, I would really appreciate learning why or why not.

By the way, I am sending back the book Moving from Windows to Linux. I have looked over Linux for Dummies and Running Linux, but I have not found an answer to my driver installation question in any of them. Am I missing something? The Linux Cookbooks look more hopeful--any book recommendations out there?

---

### Post by Gsibbery on 2005-06-04
Can you post the error messages you get here? To redirect error messages using the command line you can add something like this to it:

# command 2>error.out

The 2> redirects the error output stream to the file error.out.

---

### Post by diogena on 2005-06-04
I don't understand what you mean by redirecting an error message, but here is the message I keep getting--must be because I am not specifying where to look....

dpkg: error processing hcfpcimodem_{v.92}_{arch}.deb (--install): cannot access archive: no such file or directory
Errors were encountered while processing: hcfpcimodem_{v.92}_{arch}.deb

once I got a long list of messages, some with the word install and at the end it mentioned something about using dselect or apt...

but every other time I tried following the Linuxant site directions....I got the message I have listed above.

---

