# Introduction #

These plot tokens are the only tokens to be used cross-map.


# Details #

  * **FIND\_BOOK** - You have been told to find the spell book by the book store owner.
  * **HAS\_BOOK** - You have been given the spell book by Ash.
  * **FIND\_GHOUL\_BAIT** - Ash has authorized you to find ghoul bait.
  * **HAS\_GHOUL\_BAIT** - You have successfully purchased ghoul bait from SMART.
  * **BEGIN\_BO\_WITS** - indicates that the battle of wits has begun.
  * **DEFEAT\_MANFRED** - indicates that Manfred, the hideous monster, has been defeated.
  * **FIND\_MACIVAR\_ITEMS** - Mac Ivar has sent you to find duct tape and a swiss army knife.
  * **HAS\_MACIVAR\_ITEMS** - You have successfully purchased duct tape and a swiss army knife.
  * **MACIVAR\_FREE** - Mac Ivar is free from his cell.
  * **HAS\_MAGIC\_FLOWER** - Mac Ivar has found the magic flower and given it to you.
  * **MEMORY\_RESTORED** - indicates that Shortem's memory has been restored by the bookstore owner.
  * **NI\_ENCOUNTER** - 1:PC has met nights of Ni, 2: PC has bought Shrubbery, 3: PC has given shrubbery to knights

# Code #
## Set plot token ##
```
void main() {
  SetLocalInt(GetModule(), "<<Token Name>>", 1);
}
```
## Get plot token ##
**Testing for a conversation node:**
(Conversation node will occur if token is set to this value)
```
int StartingConditional() {
  if(GetLocalInt(GetModule(), "<<Token Name>>") == 1) {
    return TRUE;
  }
  return FALSE;
}
```


ScriptEase sets tokens a little bit differently, but equivalent to setting a boolean value.  After cleaning it up:
```
SetLocalObject(GetModule(), "<<Token Name>>", GetPCSpeaker());
```
```
if(GetLocalObject(GetModule(), "<<Token Name>>") == GetPCSpeaker()){
    return TRUE;
  }
  return FALSE;
```
This requires using a new token for each step, whereas integers allow using one token for several stages of a task.