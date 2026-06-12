---
title: "Keyboard is all screwed up"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Brutus2006 on 2006-10-31
I installed edgy but now cant do any emails or set things up with out the at symbol where did it go. 
Im new to this Linux stuff so talk english 

Thanks

---

### Post by daou on 2006-10-31
Do you have the correct keyboard layout selected in System->Preferences->Keyboard?

If you do, there might be a problem with xmodmap.

To use the correct xmodmap type

```
xmodmap /usr/share/xmodmap/xmodmap.xx 
```

where xx is the abbreviation of your country.

Type

```
ls /usr/share/xmodmap
```

and look for the abbreviation that fits with your keyboard. Mine is finnish so I use xmodmap.fi. British keyboard would probably be xmodmap.gb and so on.

---

### Post by Brutus2006 on 2006-10-31
Thank you it worked

---

