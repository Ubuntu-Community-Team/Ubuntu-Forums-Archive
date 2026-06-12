---
title: "thunar breadcrumbs redesign?"
date: 2010-03-16
forum: Art &amp; Design
---

### Post by morgengenuss on 2010-03-16
i guess almost everyone has seen the elementary nautilus breadcrumbs.
at least theoretically (as far as i understand it) this should be possible with thunar too. unfortunately i haven't managed to achieve this yet though.

for those of you who haven't seen what this should look like, check out this screenshot of nautilus old/new (this is also approximately the result i'd expect to get with thunar):
[IMG]http://img51.imageshack.us/img51/2898/yoohook.png[/IMG]


i added this code to the gtkrc of elementary (based on the information given [here]("http://thunar.xfce.org/pwiki/documentation/advanced_settings") in thunars wiki.)
maybe some of you more experienced with gtk-themes can help me out here.
```
style "thunar-pathbar" = "murrine-default"
{
	ThunarLocationButtons::spacing = 0
	engine "pixmap"
	{
		image {
			function 		= BOX
			state			= NORMAL
			file			= "nautilus/nautilus-pathbar-normal.png"
			#border			= { 0, 13, 0, 0 }
			stretch			= TRUE
		}
		image {
			function 		= BOX
			state			= PRELIGHT
			file			= "nautilus/nautilus-pathbar-prelight.png"
			border			= { 0, 13, 0, 0 }
			stretch			= TRUE
		}
		image {
			function 		= BOX
			state			= ACTIVE
			file			= "nautilus/nautilus-pathbar-active.png"
			#border			= { 0, 13, 0, 0 }
			stretch			= TRUE
		}
		#grey square fix#
		image {
			function 		= BOX
			state			= INSENSITIVE
			file			= "Others/null.png"
			#border			= { 0, 13, 0, 0 }
			stretch			= TRUE
		}
	}
}

class "ThunarLocationButtons" style "thunar-pathbar"
```

---

