---
title: "OpenOffice w/ Samba homedir?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by ckollars on 2008-03-05
I'm putting together a workstation with Gutsy Gibbon and its included OpenOffice 2.3.0. My user homedirs (rather than being local) are "mounts" from a Samba server I don't control and can't futz with or change. So far, everything works. Problem is, when I try to start any OpenOffice tool, it just shows me the splash screen and then messages "The application cannot be started. An internal error occurred." :(This seems to be because OpenOffice is trying to create a "symlink", something that won't work in the mounted home directory because the Samba server doesn't understand it. I know the Windows version of OpenOffice doesn't create symlinks; if it just did the same silliness on my Linux system it would probably work okay.  What can I do to make OpenOffice work with these Samba-shared-homedirs?

---

### Post by ckollars on 2008-03-13
After much frustrating asking and searching and grokking source code and "truss" tests, I eventually came up with what seems to be a solution. Here's what seems to work for me, interspersed with my theories as to why it works:

The only significant difference between an SMB file system and a *nix file system is the SMB file system's inability to handle symbolic links. Preventing OpenOffice from creating any symlinks will effectively allow it to run on an SMB-mounted home directory. 

The assumption that symlinks exist and the ability to create them are compiled right into the Linux version of OpenOffice.; the same compile-time options that turn on Linux compilation also turn on use of symlinks. Symlinks are so integral there appears to be no way to capture them or modify them. The only solution is to keep OpenOffice from thinking it needs to create a symlink in the first place. 

The main place OpenOffice creates symlinks is inside a new ~/.openoffice.org2. These configuration files are copied from a "template" (which exists in something like /usr/lib/openoffice/presets). If there are symlinks in the original template, OpenOffice will attempt to create similar symlinks in the per-user config copy. Conversely, if there are *not *symlinks in the original template, OpenOffice will *not *attempt to create symlinks in the per-user config. 

So to get the Linux OpenOffice to run without creating symlinks, what's needed is to legitimately get rid of all the symlinks in the template. Links are pretty easy to locate with `find` (there are twelve of them:-). They can't just be deleted though. Rather. they need to be replaced with the actual contents (and mtime) of what they used to point at. I constructed a small bash script to "unsymlink" a file, replacing a symlink by a copy of what it used to point at. (My script was pretty dumb and can be reconstructed easily. The only reason I used a script rather than doing the operations entirely manually was that manually replacing *12 *links would have taken too long and been too error prone.)

Once symlinks were legitimately removed from the OpenOffice configuration template in this way, OpenOffice came up and ran fine  ...even though the home directory was SMB-mounted.

---

