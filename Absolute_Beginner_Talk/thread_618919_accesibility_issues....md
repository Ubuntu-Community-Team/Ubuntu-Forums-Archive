---
title: "accesibility issues..."
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by arvi87 on 2007-11-20
i was a user of xp... now i have installed feisty fawn and i simply luv it... but there is jus one snag tht im really bugged wid... i created three drives initially wen i installed xp... now weneva i try to access these drives from ubuntu im prompted for my passwd... and even after i give my pwd im not able to delete or paste files on these drives... it says "cannot delete because e: is a read-only disk" so can ne1 gimme some advice on this...:confused:

---

### Post by Paul820 on 2007-11-20
You need to install ntfs-3g to get read and write permissions on your windows drives. From the terminal:
> sudo aptitude install ntfs-3g

---

