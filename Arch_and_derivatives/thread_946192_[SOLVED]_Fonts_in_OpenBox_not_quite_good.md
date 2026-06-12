---
title: "[SOLVED] Fonts in OpenBox not quite good"
date: 2008-10-13
forum: Arch and derivatives
---

### Post by kpkeerthi on 2008-10-13
I've been using [Fonts with LCD filters]("http://wiki.archlinux.org/index.php/Fonts#Fonts_with_LCD_filter_enabled") and having excellent results in GNOME. 

But for some reason, Openbox doesn't seem to honor the filters - The fonts don't look as smooth and crisp as they are in GNOME. Running **gnome-settings-daemon** in Openbox renders the font just they way they are in GNOME. But I do not want to run the daemon in the background just for the sake of it.

Is there a way to get better rendered fonts in openbox without  gnome-settings-daemon?

---

### Post by kpkeerthi on 2008-10-13
~/.fonts.conf
```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
	<match target="font" >
		<edit mode="assign" name="rgba" >
			<const>rgb</const>
		</edit>
	</match>
	<match target="font" >
		<edit mode="assign" name="hinting">
			<bool>true</bool>
		</edit>
	</match>
	<match target="font" >
		<edit mode="assign" name="hintstyle">
		<const>hintfull</const>
		</edit>
	</match> 	
</fontconfig>	

```

That fixed it!

---

