---
title: "More basic than basic"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by rpaco on 2007-06-12
How do I turn off smilies etc?
I have read the forum help and can find nowhere where it says how to do this. It is not in CP, not showing on my Firefox V2.0.0.4 anyway. There is a reference elsewhere to the  "turn the smiley off option when posting" but again no hint as to where it is. Clicking on the Posting Rules codes has no effect.
Please point.

---

### Post by phr0ze on 2007-06-12
It would logically belong here in User Options, Thread Display Options. However the option does not exist. So you can't.

---

### Post by rpaco on 2007-06-12
It needs to be available when posting
Posting Rules show which is on or off but not how to select them.
When posting output from a terminal it must often be necessary to turn smilies off. (as was my case yesterday,  a sad face in the middle of a line of text)

It must be there somewhere I cant believe the forum guys forgot it !

---

### Post by lazyart on 2007-06-12
Hit Post Reply (instead of the usual quick reply).  Roll down the screen and you will see the option to disable smileys in text.

In the future, please title threads relevant to the content. "More basic than basic" doesn't give a bit of a hint to the topic.

---

### Post by mcduck on 2007-06-12
Just put all commands and terminal output inside code tags (the #-symbol when posting here). That way it gets no formatting or smilies, and also if the lines are long the code block becomes scrollable instead of breaking the forum layout.

---

### Post by Wim Sturkenboom on 2007-06-12
> **mcduck said:**
> Just put all commands and terminal output inside code tags (the #-symbol when posting here). That way it gets no formatting or smilies, and also if the lines are long the code block becomes scrollable instead of breaking the forum layout.Just to check:
```

for(;;)
{
}

```

---

### Post by rpaco on 2007-06-13
Hi thanks for your suggestions, however:

McDuck sounds good, but  your suggestion does not work, thus:
#abcedef;)ghijk# 

Lazyart I already said there are no apparent visible options to disable smilies anywhere on the page whether in quick or regular post mode. The only options shown are:

Ubuntu Bug URL (optional)
Post icons ("No icon" is  selected in my case)

Additional options
Automatically parse links in text
Attach files
Thread subscription.

Please state whereabouts on the screen the "disable  smilies" option is supposed to be. ie immediately above or below what and/or left or right of what. Come to that there must be somewhere to turn all the other codes on or off ie the IMG HTLM and vB

To reproduce Wim's check it does this for me:
#(;;)# so please tell me what I am doing wrong.

Meanwhile I cannot post the output from a terminal in another query I have running.

---

### Post by mcduck on 2007-06-13
Not the actual # from your keyboard, but the button in the reply window that has # on it.. ;)

---

### Post by lazyart on 2007-06-13
> **rpaco said:**
> 
Lazyart I already said there are no apparent visible options to disable smilies anywhere on the page whether in quick or regular post mode. The only options shown are:

Ubuntu Bug URL (optional)
Post icons ("No icon" is  selected in my case)

Additional options
Automatically parse links in text
Attach files
Thread subscription.

Please state whereabouts on the screen the "disable  smilies" option is supposed to be. ie immediately above or below what and/or left or right of what. Come to that there must be somewhere to turn all the other codes on or off ie the IMG HTLM and vB


Use Post Reply, like I said and you will find it in the Additional Options section.  See the attached image.

The other option is to use CODE and /CODE tags to encapsulate your output.  It's better than disabling smilies anyway.

Look, smiley off: :) :D ;) :o

---

### Post by stalkingwolf on 2007-06-13
under additional options you should see,

 Miscellaneous Options
Show your signature
Automatically parse links in text
Disable smilies in text

---

### Post by rpaco on 2007-06-13
Hi guys well I must be running different versions than you. 

1) There are no buttons in the reply window (either the quick or regular)
2) There is only the "Automatically parse links in text" option  in my Miscellaneous options.

I am running this (Taken from Firefox Help>About) 
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20060601 Firefox/2.0.0.4 (Ubuntu-edgy)

So sorry for appearing incredibly thick, but this forum is obviously not displaying the same for everyone.

I herewith try and show a chunk of the page source code which clearly has only one option in Miscellaneous options:
<CODE> 
			
	<div style="margin-top:6px">
		<input type="hidden" name="s" value="" />

		<input type="hidden" name="do" value="postreply" />
		<input type="hidden" name="t" value="471787" />
		<input type="hidden" name="p" value="2829821" />
		<input type="hidden" name="posthash" value="6956a635b3063a8d921c9adf1edcf3a7" />
		<input type="hidden" name="poststarttime" value="1181749556" />
		<input type="hidden" name="loggedinuser" value="260159" />
		<input type="hidden" name="multiquoteempty" id="multiquote_empty_input" value="" />
		<input type="submit" class="button" name="sbutton" id="vB_Editor_001_save" value="Submit Reply" accesskey="s" tabindex="1" />
		<input type="submit" class="button" name="preview" value="Preview Post" accesskey="r" tabindex="1" />

	</div>
	</td>
</tr>
</table>


<br />

<table class="tborder" cellpadding="6" cellspacing="0" border="0" width="100%" align="center">
<thead>
	<tr>
		<td class="tcat">
			<a style="float:right" href="#top" onclick="return toggle_collapse('newpost_options')"><img id="collapseimg_newpost_options" src="http://ubuntuforums.org/images/uf/buttons/collapse_tcat.gif" alt="" border="0" /></a>

			Additional Options
		</td>
	</tr>
</thead>
<tbody id="collapseobj_newpost_options" style="">	
	<tr valign="top">
		<td class="panelsurround" align="center">
		<div class="panel">
			<div style="width:640px" align="left">
							
				
				<fieldset class="fieldset">
					<legend>Miscellaneous Options</legend>

					<div style="padding:3px">
						
						<div><label for="cb_parseurl"><input type="checkbox" name="parseurl" value="1" id="cb_parseurl" tabindex="1" checked="checked" />Automatically parse links in text</label></div>
						
					</div>
				</fieldset>
				
	
				<fieldset class="fieldset">
	<legend>Attach Files</legend>
	<div style="padding:3px">
		<div style="margin-bottom:3px">

			<div>Valid file extensions: bmp bz2 deb doc gif gpl gz jpe jpeg jpg odg odp ods odt pdf png psd py sh svg tar txt xcf zip</div>
		</div>
		<div style="margin-bottom:3px" id="attachlist">
			
		</div>
		<div>
			<script type="text/javascript" src="clientscript/vbulletin_attachment.js?v=367"></script>
			<script type="text/javascript">
			<!--
			var newpost_attachmentbit = '<div style="margin:2px">\r\n	<img class="inlineimg" src="%1$s" alt="" border="0" />\r\n	<a href="attachment.php?attachmentid=%3$s&amp;stc=1&amp;d=%4$s" target="_blank">%5$s</a>\r\n	(%6$s)\r\n</div>';
			vB_Attachments = new vB_Attachment('attachlist', '');
			
			document.write('<input type="button" id="manage_attachments_button" class="button" tabindex="1" style="font-weight:normal" value="Manage Attachments" title="Click here to add or edit files attached to this message" onclick="vB_Attachments.open_window(\'newattachment.php?t=471787&amp;poststarttime=1181749556&amp;posthash=6956a635b3063a8d921c9adf1edcf3a7\', 480, 480, \'2829821\')" />');
			//-->
			</script>

			<noscript>
			<a href="newattachment.php?t=471787&amp;poststarttime=1181749556&amp;posthash=6956a635b3063a8d921c9adf1edcf3a7" target="manageattach" title="Click here to add or edit files attached to this message" tabindex="1"><strong>Manage Attachments</strong></a>
			</noscript>
		</div>
	</div>
</fieldset>
</CODE>

Sorry again, how do you use the CODE /CODE I have tried it with and without chevrons, don't tell me,,,,, another button that I dont have!

---

### Post by mcduck on 2007-06-13
> **rpaco said:**
> 
Sorry again, how do you use the CODE /CODE I have tried it with and without chevrons, don't tell me,,,,, another button that I dont have!
In forums tags use [ and ] instead of < and >. So it's [CODE] (and the close tag in the same way).

---

### Post by rpaco on 2007-06-13
Code trial
```
rpa@rpaco-pc:~$ wine taxcalc
fixme:shdocvw:PersistStreamInit_InitNew (0x173ab0)
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x173ab0)
fixme:shdocvw:OleObject_Close (0x173ab0)->(1)
err:seh:setup_exception nested exception on signal stack in thread 0009 eip 7bc58333 esp 7ffddbf0 stack 0x231000-0x340000
rpa@rpaco-pc:~$ 

```

Ok it works, thanks I think I have got the hang of it now, but no answer to the missing buttons. I am wondering if different servers are putting out slightly different pages. as you can see from the page source I posted in my previous post, there are definitely bits missing, compared to the screenshot posted by you earlier.

Anyway using code tabs I can now go back to my original wine problem in another thread.
Many thanks to all.

---

### Post by mcduck on 2007-06-13
For the different message editor in these forums, try this: go to User CP/Edit Options. NEar the bottom of the page there's option for Message Editor Interface,giving three options, Basic Editor, Standard Editor and Enhanced Interface. If that is set to Basic Editor you won't have too much tools when writing a message to these forums. Try setting it to either Standard or Enhanced. (I have it on Standard).

---

### Post by tamays on 2007-06-21
Where the !@#$% is the POST or NEW POST Button? One shouldn't have to go searching for such a button, it should be right on the !@#$% page!

---

### Post by lazyart on 2007-06-21
> **tamays said:**
> Where the !@#$% is the POST or NEW POST Button? One shouldn't have to go searching for such a button, it should be right on the !@#$% page!

Don't go into a thread if you want to post a new thread.  If you go out to the threads list, the button is under the brown bar.

See the attached image.  And watch your language.  Do you kiss your mother with that mouth?

---

