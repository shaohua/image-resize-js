To do client-side image resizing you need to include the following scripts:  
(Please note that you should download and upload all resources to your own server and not reference source files from the **blueimp.github.io** domain.)

```html
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.10.1/jquery.min.js"></script>
<!-- The jQuery UI widget factory, can be omitted if jQuery UI is already included -->
<script src="js/vendor/jquery.ui.widget.js"></script>
<!-- The Load Image plugin is included for the preview images and image resizing functionality -->
<script src="https://blueimp.github.io/JavaScript-Load-Image/js/load-image.all.min.js"></script>
<!-- The Canvas to Blob plugin is included for image resizing functionality -->
<script src="https://blueimp.github.io/JavaScript-Canvas-to-Blob/js/canvas-to-blob.min.js"></script>
<!-- The Iframe Transport is required for browsers without support for XHR file uploads -->
<script src="js/jquery.iframe-transport.js"></script>
<!-- The basic File Upload plugin -->
<script src="js/jquery.fileupload.js"></script>
<!-- The File Upload processing plugin -->
<script src="js/jquery.fileupload-process.js"></script>
<!-- The File Upload image preview & resize plugin -->
<script src="js/jquery.fileupload-image.js"></script>
```

Then, all you need to do is to set the option **disableImageResize** to *false*.  
By default, images are resized to FullHD (1920x1080), but you can define your own [[Options]]:

```js
$('#fileupload').fileupload({
    url: '//jquery-file-upload.appspot.com/',
    dataType: 'json',
    // Enable image resizing, except for Android and Opera,
    // which actually support image resizing, but fail to
    // send Blob objects via XHR requests:
    disableImageResize: /Android(?!.*Chrome)|Opera/
        .test(window.navigator && navigator.userAgent),
    imageMaxWidth: 800,
    imageMaxHeight: 800,
    imageCrop: true // Force cropped images
})
```