require 'rubygems'
require 'rake'
require 'bundler'
begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "padrino-warden"
    gem.summary = %Q{authentication system for using warden with Padrino, adopted from sinatra_warden}
    gem.description = %Q{basic helpers and authentication methods for using warden with padrino also providing some hooks into Rack::Flash}
    gem.email = "dotan@paracode.com"
    gem.homepage = "http://github.com/jondot/padrino-warden"
    gem.authors = ["Dotan Nahum"]
    bundle = Bundler::Definition.from_gemfile('Gemfile')
    bundle.dependencies.each do |dep|
      next unless dep.groups.include?(:runtime)
      gem.add_dependency(dep.name, dep.version_requirements.to_s)
    end
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: gem install jeweler"
end

require 'spec/rake/spectask'
Spec::Rake::SpecTask.new(:spec) do |spec|
  spec.libs << 'lib' << 'spec'
  spec.spec_files = FileList['spec/**/*_spec.rb']
end

Spec::Rake::SpecTask.new(:rcov) do |spec|
  spec.libs << 'lib' << 'spec'
  spec.pattern = 'spec/**/*_spec.rb'
  spec.rcov = true
end

task :spec => :check_dependencies

task :default => :spec

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "padrino-warden #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
