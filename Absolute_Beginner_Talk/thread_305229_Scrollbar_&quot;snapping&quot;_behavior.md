---
title: "Scrollbar &quot;snapping&quot; behavior?"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by sirjis on 2006-11-23
I recently installed ubuntu alongside windows on my laptop, and it's working quite nicely.  Any major troubles I've had have already been discussed, but there's just one small thing that annoys me.  When I use a scrollbar by dragging the thumb in Windows, if I move my mouse far enough away from the scrollbar, it will snap back to the position it was in before scrolling.  I suppose people not used to this might find it annoying, but I've grown accustomed to using it to read something above on a website without losing my position, for example.  Is there any way to enable this behavior on ubuntu?

Thanks!

---

### Post by rlozano on 2006-11-23
> **sirjis said:**
> I recently installed ubuntu alongside windows on my laptop, and it's working quite nicely.  Any major troubles I've had have already been discussed, but there's just one small thing that annoys me.  When I use a scrollbar by dragging the thumb in Windows, if I move my mouse far enough away from the scrollbar, it will snap back to the position it was in before scrolling.  I suppose people not used to this might find it annoying, but I've grown accustomed to using it to read something above on a website without losing my position, for example.  Is there any way to enable this behavior on ubuntu?

Thanks!

im not sure if that is an OS feature or mouse specific.

---

### Post by adam.tropics on 2006-11-23
..or perhaps browser specific?

---

### Post by sirjis on 2006-11-23
I'm pretty sure this is an OS feature (gtk+, at least).  It occurs in almost all programs with scrollbars (including gedit). This is the first time I've looked through any source code of this scale, so bear with me if I'm looking in the totally wrong location.  

I decided to look at the gedit source code (using google code search) and it seemed like they didn't do anything with scrolling (stuff like subtracting the mouse y-position from the starting y-position).  So I figure that this behavior is probably in gtk, considering the call to the gtk_scrolled_window_new() function in gedit.

After searching through window.cpp, and scrolbar.cpp [sic] (which I now realize are actually in the wxWidgets library...I'm not sure where that fits into the gnome/gtk+ picture), I ended up at the gtkrange.c file, which seems to be exactly what I've been looking for.  It contains the following two functions

```

static gint
gtk_range_motion_notify (GtkWidget      *widget,
			 GdkEventMotion *event)
{
  GtkRange *range;
  GdkModifierType mods;
  gint x, y, mask;

  g_return_val_if_fail (widget != NULL, FALSE);
  g_return_val_if_fail (GTK_IS_RANGE (widget), FALSE);
  g_return_val_if_fail (event != NULL, FALSE);

  range = GTK_RANGE (widget);

  if (range->click_child == RANGE_CLASS (range)->slider)
    {
      x = event->x;
      y = event->y;

      if (event->is_hint || (event->window != range->slider))
	gdk_window_get_pointer (range->slider, &x, &y, &mods);
      else
	mods = event->state;

      // <snip>

      if (mods & mask)
	{
	  if (RANGE_CLASS (range)->motion)
	    (* RANGE_CLASS (range)->motion) (range, x - range->x_click_point, y - range->y_click_point);
	}
    }

  return FALSE;
}

```
This code seems to be where the actual subtraction is done that I had been looking for.  

This one also seems important (I couldn't tell if this is what's eventually being called by that *range->motion function pointer at the end of the code above, but the type signatures seem to match, so that's what I'm guessing.

```

void
gtk_range_default_vmotion (GtkRange *range,
			   gint      xdelta,
			   gint      ydelta)
{
  gdouble old_value;
  gint top, bottom;
  gint slider_x, slider_y;
  gint new_pos;

  g_return_if_fail (range != NULL);
  g_return_if_fail (GTK_IS_RANGE (range));

  range = GTK_RANGE (range);

  gdk_window_get_position (range->slider, &slider_x, &slider_y);
  gtk_range_trough_vdims (range, &top, &bottom);

  if (bottom == top)
    return;

  new_pos = slider_y + ydelta;

  if (new_pos < top)
    new_pos = top;
  else if (new_pos > bottom)
    new_pos = bottom;

  old_value = range->adjustment->value;
  range->adjustment->value = ((range->adjustment->upper -
			       range->adjustment->lower -
			       range->adjustment->page_size) *
			      (new_pos - top) / (bottom - top) +
			      range->adjustment->lower);

  if (range->digits >= 0)
    {
      char buffer[64];

      sprintf (buffer, "%0.*f", range->digits, range->adjustment->value);
      sscanf (buffer, "%f", &range->adjustment->value);
    }

  if (old_value != range->adjustment->value)
    {
      if (range->policy == GTK_UPDATE_CONTINUOUS)
	{
	  gtk_signal_emit_by_name (GTK_OBJECT (range->adjustment), "value_changed");
	}
      else
	{
	  gtk_range_slider_update (range);
	  gtk_range_clear_background (range);

	  if (range->policy == GTK_UPDATE_DELAYED)
	    {
	      gtk_range_remove_timer (range);
	      range->timer = gtk_timeout_add (SCROLL_DELAY_LENGTH,
					      (GtkFunction) RANGE_CLASS (range)->timer,
					      (gpointer) range);
	    }
	}
    }
}

```
(I'm curious about the use of sprintf and sscanf here...)


The reason why I went through all of this (besides the benefit of learning) was to figure out where the scrollbar mouse motion work is being done.  It seems to me that there is no effort to look for horizontal offset in a vertical scrollbar.  To fix* this would seem to simply require using the xdelta parameter inside the gtk_range_default_vmotion function (and probably the ydelta in the hmotion for consistency), and saving the scroll value from  the most recent mouse-down, if it's not already being done.

*IMHO...I am open to discussion of reasons for not implementing this change.

Now, I realize that the coders have a lot of work on their hands, and making a minor change like this is probably not high on their list.  Where is the best place to make a feature request? (Or even is it possible for me to modify something like this myself?).

This topic no longer seems to be suited for this section of the forum.  I was originally hoping for a quick answer, but now I've made it pretty technical.  Please move it if you see fit.

---

