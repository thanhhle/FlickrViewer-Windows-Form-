# FlickrViewer
An application written in C#

## Description
Create a Flickr Viewer app that allows users to search for photos on the photo-sharing website Flickr then browse through the result. The app uses an ansynchronous method to invoke a Flickr web service. The Flickr Viewer app allows user to search by tag for photos that users worldwide have uploaded to Flickr.

## Implementation
To access the Flickr web service on your computer, you must obtain your own Flickr API key at http://www.flickr.com/services/apps/create/apply

You are going to invoke the Flickr web service's method flickr.photos.search. You can learn more about this web-service method's parameters and the format of the URL for invoking the method at https://www.flickr.com/services/api/flickr.photos.search.html

In this program, you specify values for the following parameters:
- api_key (Required)
- tags: A comma-delimited list of tags. Photos with one or more of the tags listed will be returned. You can exclude results that match a term by prepending it with a - character.
- tag_mode: Either 'any' for an OR combination of tags, or 'all' for an AND combination. Defaults to 'any' if not specified.
- per_page: Number of photos to return per page. If this argument is omitted, it defaults to 100. The maximum allowed value is 500.
- privacy_filter (Optional): Return photos only matching a certain privacy level. This only applies when making an authenticated call to view photos you own. Use value 1.

The method flickr.photos.search returns the standard photo list xml:
```
<?xml version="1.0" encoding="utf-8" ?>
<rsp stat="ok">
  <photos page="1" pages="2723" perpage="100" total="272227">
    <photo id="49020483403" owner="35648055@N02" secret="9017c45e28" server="65535" farm="66" title=""Fine, I'll sit"" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49021209057" owner="35648055@N02" secret="de16a01fe3" server="65535" farm="66" title="Unstoppable" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49021134557" owner="136874576@N07" secret="0657f29697" server="65535" farm="66" title="small Isla big hug" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49020901141" owner="148317128@N05" secret="be978dff98" server="0" farm="0" title="MVI_3904" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49020904911" owner="9772325@N04" secret="d68b41985a" server="65535" farm="66" title="Jessie" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49020782987" owner="146584730@N05" secret="5de9054bcb" server="65535" farm="66" title="Wifi" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49020762767" owner="32916154@N00" secret="f6cafebf37" server="65535" farm="66" title="361/365 11/05/19 Pug Figurine" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49020754952" owner="166078916@N06" secret="4abf983392" server="65535" farm="66" title="sam" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49020714347" owner="169904704@N04" secret="0cdc68ed75" server="65535" farm="66" title="😎 Little Red Riding Hood 😊" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49019970118" owner="55106585@N04" secret="9847e8209d" server="65535" farm="66" title="Hey you" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49019955278" owner="134241793@N03" secret="56bcda5587" server="65535" farm="66" title="Little dog" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49019842348" owner="185366461@N02" secret="420c4ffe68" server="65535" farm="66" title="IMG_0093" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49020539767" owner="104161577@N06" secret="6be4d3a6dc" server="65535" farm="66" title="falling leaves" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49019681063" owner="7512717@N06" secret="99c88cbbb8" server="65535" farm="66" title="Lovely Day For a Dog Walk 01" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49020402422" owner="7512717@N06" secret="5a43e3f94b" server="65535" farm="66" title="Lovely Day For a Dog Walk 02" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49020189366" owner="185385304@N06" secret="fcdd0d76f5" server="65535" farm="66" title="Blessing of the Animals-60" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49019556918" owner="50109591@N06" secret="d58e5c7080" server="65535" farm="66" title="Sakara" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49019994291" owner="57787151@N08" secret="ca6de82d87" server="65535" farm="66" title="Smooth" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49019994186" owner="57787151@N08" secret="4084dffcb7" server="65535" farm="66" title="The chase" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49019443393" owner="182341655@N03" secret="913aef2bae" server="65535" farm="66" title="WERA Exotic World FCI" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49020159117" owner="182341655@N03" secret="eebcfdcf00" server="65535" farm="66" title="WERA Exotic World FCI" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49019434498" owner="182341655@N03" secret="fc9d7705ca" server="65535" farm="66" title="WERA Exotic World FCI" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49019432903" owner="182341655@N03" secret="eeeb62b780" server="65535" farm="66" title="WERA Exotic World FCI" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49020151037" owner="182341655@N03" secret="828648d090" server="65535" farm="66" title="WERA Exotic World FCI" ispublic="1" isfriend="0" isfamily="0" />
    <photo id="49018253756" owner="122226435@N06" secret="f529d6c2ae" server="65535" farm="66" title="a furry dog" ispublic="1" isfriend="0" isfamily="0" />
  </photos>
</rsp>
```

#### REST Request Format
- REST is the simplest request format to use - it's a simple HTTP GET or POST action.
- The REST Endpoint URL is https://api.flickr.com/services/rest/
- To request the flickr.test.echo service, invoke like this: https://api.flickr.com/services/rest/?method=flickr.test.echo&name=value
