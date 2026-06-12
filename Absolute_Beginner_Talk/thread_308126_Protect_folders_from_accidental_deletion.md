---
title: "Protect folders from accidental deletion"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by Quicky on 2006-11-27
Is the a method to protect folders within the home folder so that they cannot be deleted? For example; I have a series of folders (pictures, documents, music etc) the contents of which I modify frequently, but I would like to make sure that I never accidentally delete the folders themselves.

Can this be done using permissions, or is there another method?

---

### Post by hearnden on 2006-11-27
The deletability of a folder's contents are controlled by that folder's write-permission bits.  So to prevent a folder within the home folder being deleted, you'd have to make your home folder non-writable, which may or may not be a problem for you (it would, for example, prevent the creation of new folders within your home folder).  This would not prevent the *contents* of that folder being deleted however.  The only way to do that would be either to make the folder non-writable (which would prevent new contents being created), or to make all of the contents non-writable (which would prevent each of them from being deleted or modified).  None of these seem to fit with your desire to frequently modify such folders' contents (except for making your home folder non-writable, which will not prevent the contents of such subfolders being deleted).

I'd suggest that your fear of those folders getting accidentally deleted is perhaps too high.  The only way I can think of that you'd accidentally delete such folders would be from an accidental recursive deletion of your home folder (I don't know anyone who has ever done this), or accidentally selecting a bunch of folders and hitting the delete button (in which case you can recover them from the Trash).

If you're still worried about accidentally deleting them, then I'd suggest putting such things in a location that you *won't* delete, e.g. /data/pictures, /data/documents, ..., and creating symbolic links from your home folder:
```

$ cd
$ ln -s /data/documents
$ ln -s /data/pictures

```

That way, if you accidentally 'rm -rf' from your home folder, it will only delete the links but not what they link to, so /data/documents etc will still be there.

---

### Post by Quicky on 2006-11-27
I thought as much, but I guess that's not much use to me since I'd like to be able to write/delete/modify the rest of the home folder contents.

---

### Post by CatKiller on 2006-11-27
The symbolic link idea is a good one. It will behave just like a normal directory, except that you'll only unlink it instead of deleting it if you try to delete it accidentally.

I also concur with hearnden that you aren't that likely to delete them permanently accidently. Well, there's always schizophrenia, I suppose... But there's the wastebasket for recovery of things that you delete through the GUI.

---

