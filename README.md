# browserSyncScript
gulp script to use browser sync with tomcat server (java backend)
<hr>

<code>
var gulp = require('gulp');
var browserSync = require('browser-sync').create();

gulp.task('default',['copyToServer'], function() {
  gulp.watch('WebContent/**/*.{html,js,css}',['copyToServer']);

  browserSync.init({
    proxy: "http://localhost:8080/TestingBrowserSync/"
  });

});

gulp.task('copyToServer', function() {
  gulp.src('WebContent/**/*.{html,js,css}')
    .pipe(gulp.dest('you-path/apache-tomcat-8.0.39/webapps/TestingBrowserSync'))
    .pipe(browserSync.stream());
});

</code>
