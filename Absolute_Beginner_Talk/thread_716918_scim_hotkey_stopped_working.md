---
title: "scim hotkey stopped working"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by chiisana on 2008-03-06
I had scim configured all working following this instruction:
[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

However, I wasn't too pleased with the Traditional Chinese's roman pinyin input (Phonetic works great; but pinyin was bad-ish because it didn't seem to like mixed input with even punctuation symbols), so I looked for alternatives.  Eventually, I located fcitx; and followed this Chinese guide to install it on my system:
[http://wiki.ubuntu.org.cn/index.php?title=%E4%B8%AD%E6%96%87%E8%BE%93%E5%85%A5%E6%B3%95fcitx&variant=zh-tw](http://wiki.ubuntu.org.cn/index.php?title=%E4%B8%AD%E6%96%87%E8%BE%93%E5%85%A5%E6%B3%95fcitx&variant=zh-tw)

Unfortunately, after installing it, it simply refused to input anything; even if I set the IME to that.  As such, I decided to remove it using
```
sudo apt-get remove fcitx
```

This removed the fcitx, but it didn't quite restore SCIM for me, then I realized I didn't restore the changed im-switch settings; so I did these:
```

sudo im-switch -s scim -z default
im-switch -s scim -z default

```

After rebooting (logging out and logging back in might've done the trick, too) brought back the SCIM toolbar floating thing, but it doesn't actually seem to like any of the hotkeys.  I've tried to change, save and reload the configurations, and  it doesn't seem to attach the hook back, too.

Is there anything I'm missing that I should've done, so that the hotkeys come back :confused:

---

### Post by chiisana on 2008-03-10
Replying to my own issue.

This was resolved by setting the default IM to "scim" instead of "scim-bridge" in the xinput.d file.

---

### Post by seshomaru samma on 2008-03-10
btw- you can't run scim and fcitx at the same time

---

