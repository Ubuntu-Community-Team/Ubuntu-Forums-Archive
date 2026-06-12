---
title: "Installing Ubuntu on a Macbook with Linux Mint"
date: 2013-10-31
forum: Apple Hardware Users
---

### Post by timebandit11 on 2013-10-31
I have a Macbook which I installed Linux Mint on a while back.  I did not use a partition to keep OSX on it, so it only has Linux Mint.  I decided I'd like to install Ubuntu on it, but I cannot get the Macbook to boot Ubuntu from DVD or USB.  I installed rEFIt on it, which is how I installed Linux Mint on it in the first place, but now I can't access rEFIt.  Any ideas?

---

### Post by mpbishop on 2013-11-05
What version of MacBook do you have? Here's a few generic things to try:

*(As a precursor to these suggestions, I recommend in the future to always keep a small OS X partition on your drive in case you ever need to troubleshoot, even if you never use it for anything else. My instructions below will reflect this practice. Personally, I left a 32GB partition for a stock OS X install for this express purpose, and devoted the rest of my 512GB drive to Ubuntu. Your situation may be different, but I highly recommend keeping a small section of your hard drive devoted to OS X, just in case.)*

**Internet Recovery**
1. Plug in an ethernet cord that is connected to a live internet connection. Hold down the 'Option' key right after you power on the MacBook. Keep it held and see if a boot menu appears with a globe icon. If so, this is OS X's "Internet Recovery" feature, which you can use to re-install OS X (as well as run tools like 'Disk Utility' to wipe/reset your partitions). Once OS X is up and running again, you should be able to resize your drive's partion within OS X, then install rEFInd (don't use rEFIt, it's no longer supported), and finally, install Ubuntu. Only newer MacBook models support Internet Recovery mode, though, so this may not work.

_Note_: If this does not work, and you have the ability to pull the hard drive out and put it into an external reader on another computer, do so and completely erase/wipe the drive from an external computer, then place it back in your MacBook and try again. I've sometimes experienced that Internet Recovery won't work unless the Hard Drive is completely wiped clean as if you just unboxed it.


**USB Recovery**
1. If the above option fails, try creating a USB Recovery drive from another Mac using this program from Apple: [http://support.apple.com/kb/DL1433](http://support.apple.com/kb/DL1433). This is, of course, assuming you have another Mac with which to do this. If not, just ask a friend - or visit your local Starbucks and offer to buy a coffee for one of the dozen Apple users you are pretty much guaranteed to see inside, in exchange for a few minutes on their computer. Of course, you'll have to assure them that your need for their MacBook is totally legit, and that you aren't secretly installing some spyware on their system. Hehe.

2. Once you have a USB recovery drive made, try to get OS X installed again using it (hold down 'Option' during bootup and select it), then shrink the partition to the minimal size necessary using 'Disk Utility', then install rEFInd, and finally get going on your Ubuntu installation again. (Note that within the recovery utility that you first boot into, you may need to first fire up 'Disk Utility' and erase/set your hard drive back to a single partition for OS X, in order to complete the installation).



If neither of these methods work, post what your specific MacBook version is and I'll see if I can't come up with any more tricks you can try.

---

### Post by mpbishop on 2013-11-05
I should probably also say that my suggestions above are assuming that you don't have any data currently on the hard drive that you don't mind losing, since you'll be wiping/resetting the drive's partitions and filesystem(s). If you DO have important data currently on the hard drive, BACK IT UP FIRST! :P

---

