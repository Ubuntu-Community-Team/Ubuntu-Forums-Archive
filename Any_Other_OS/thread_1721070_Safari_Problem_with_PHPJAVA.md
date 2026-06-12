---
title: "Safari Problem with PHP/JAVA"
date: 2011-04-04
forum: Any Other OS
---

### Post by dazman19 on 2011-04-04
This works MINT in Firefox, but i need to support iphones. 

The onclick event does not happen in safari but i get no javascript errors in firebug or safari debugger.

Can anyone help? I dont code for safari much and have spend ages trying to fix it.

[PHP]        <li>Start Time: <br /><input name="startDatedd" id="startDatedd" maxlength="2" style="width:18px;" type="text" value="<?php echo date(d); ?>"><input name="startDatemm" id="startDatemm" style="width:18px;" maxlength="2" type="text" value="<?php echo date(n); ?>"><input name="startDateyy" id="startDateyy" maxlength="4" style="width:30px;" type="text" value="<?php echo date(Y); ?>">H:<select name="startTimehh" id="startTimehh" ><?php for($i =0; $i < 24; $i++) { echo "<option value=\"".($i * 60)."\">".$i."</option>"; } ?></select>M:<select name="startTimemm" id="startTimemm" ><?php for($i = 0; $i < 4; $i++) { echo "<option value=\"".($i * 15)."\">".($i*15)."</option>"; } ?></select></li>
        <li>End Date:<br /><input name="endDatedd" id="endDatedd" maxlength="2" style="width:18px;" type="text" value="<?php echo date(d); ?>"><input name="endDatemm" id="endDatemm" style="width:18px;" maxlength="2" type="text" value="<?php echo date(n); ?>"><input name="endDateyy" id="endDateyy" style="width:30px;" maxlength="4" type="text" value="<?php echo date(Y); ?>">H:<select name="startTimehh" id="startTimehh" ><?php for($i =0; $i < 24; $i++) { echo "<option value=\"".($i * 60)."\">".$i."</option>"; } ?></select>M:<select name="startTimemm" id="startTimemm" ><?php for($i = 0; $i < 4; $i++) { echo "<option value=\"".($i * 15)."\">".($i*15)."</option>"; } ?></select></li>
        <li>Template:
        <?php $templates = WorkDoneTemplate::getAllWhere("workdonetemplatedata_active ='1'"); ?>
            <select style="float:right;" name="template" id="template"><option></option>
            <?php foreach ($templates as $template) {
                echo
                "<option value=\"$template->workdonetemplate_id\" onclick=\"document.getElementById('workdonet').value='".(Formatting::jssafe($template->workdonetemplatedata_name))."';document.getElementById('workdone').value='".(Formatting::jssafe($template->workdonetemplatedata_content))."';return false;\" >
                    $template->workdonetemplatedata_name
                </option>";} ?>
        </select></li>
        <?php ?>
        <li>Work Done Title:<input id="workdonet" style="float:right;" type="text" name="workdonet"  /></li>
        <li>Work Desc: <input id="workdone" style="float:right;" type="text" name="workdone"  value=""/></li>

        <div id="jaxresponse"></div>
        <li><input style="width:98%;" class="whiteButton" value="Add Time" type ="button" onclick="existjobjax();"></li>
    </ul>
<script type="application/javascript">document.ready;</script>[/PHP]

The actual returned stuff in the browser is:

[PHP]<li>Template:
                    <select style="float:right;" name="template" id="template"><option></option>
            <option value="1" onclick="document.getElementById('workdonet').value='Mapped Drives in Citrix';document.getElementById('workdone').value='Remapped a drive in Citrix.';return false;" >
                    Mapped Drives in Citrix
                </option><option value="2" onclick="document.getElementById('workdonet').value='Citrix - Permissions';document.getElementById('workdone').value='No permissions allowed for user in Citrix Mapped Drive';return false;" >
                    Citrix - Permissions
                </option><option value="3" onclick="document.getElementById('workdonet').value='Medtech Scanning';document.getElementById('workdone').value='Pushed through the scanning.';return false;" >
                    Medtech Scanning
                </option><option value="4" onclick="document.getElementById('workdonet').value='Reset Terminal Sessions';document.getElementById('workdone').value='Reset terminal sessions for users.';return false;" >
                    Reset Terminal Sessions
                </option><option value="5" onclick="document.getElementById('workdonet').value='Lotus Notes \'To\' Field';document.getElementById('workdone').value='Lotus Notes would not automatically fill out the recipients email address when typing in  the \'To\' field.\n\nChanged settings to check after every letter typed, check local then server, and always search all address books.\n\nWorking now.';return false;" >
                    Lotus Notes 'To' Field
                </option>        </select></li>
                <li>Work Done Title:<input id="workdonet" style="float:right;" type="text" name="workdonet"  /></li>
        <li>Work Desc: <input id="workdone" style="float:right;" type="text" name="workdone"  value=""/></li>

        <div id="jaxresponse"></div>
        <li><input style="width:98%;" class="whiteButton" value="Add Time" type ="button" onclick="existjobjax();"></li>
    </ul>
<script type="application/javascript">document.ready;</script>
[/PHP]

---

### Post by dazman19 on 2011-04-04
Sorry this should read javascript

---

