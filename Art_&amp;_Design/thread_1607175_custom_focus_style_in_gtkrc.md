---
title: "custom focus style in gtkrc"
date: 2010-10-27
forum: Art &amp; Design
---

### Post by Interruptor on 2010-10-27
```
style "default" {
	engine "pixmap" {
		image {
			function		= FOCUS
			recolorable		= TRUE
			detail			= "button"
			file			= "button-focus.png"
			border			= {4, 4, 4, 4}
			stretch			= TRUE
		}
	}
}

class "GtkWidget" style "default"
```
from "New Wave" theme.

---

